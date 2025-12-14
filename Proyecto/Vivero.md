# Documento de Diseño de Sistema: Vivero AI & Trazabilidad

#### Objetivo General
Desarrollar una **Plataforma Web Integral** accesible desde cualquier dispositivo móvil (navegador), diseñada para digitalizar el proceso de cosecha, pago a operarios y trazabilidad de estacas de vid. El sistema elimina el conteo manual propenso a errores mediante **Inteligencia Artificial** y transforma procesos biológicos complejos en un flujo logístico de estados simple y auditable.
#### Pilares Funcionales
***1. Cosecha Inteligente (AI-Powered)***
- **El Problema:** El conteo manual de estacas es lento, tedioso y genera desconfianza en los pagos.
- **La Solución:** El encargado toma una foto a los atados de estacas usando la Web App. Un modelo de IA (**YOLOv8**) procesa la imagen y devuelve el conteo exacto.
- **Interacción:** El usuario valida visualmente el conteo (con "cajas" dibujadas sobre la imagen) y confirma. Esto genera automáticamente la liquidación para el cosechador (pago por tanto) y el ingreso de stock.

***2. Trazabilidad (Máquina de Estados)***
- **Concepto de Lote:** Cada contenedor (Bin) es un "Lote" único digital.
- **Seguimiento:** En lugar de flujos complejos, el sistema gestiona la vida del lote mediante **Cambios de Estado/Ubicación**: _Origen -> Cámara de Frío -> Taller -> Campo -> Venta_.
- **Genealogía (Injerto):** El sistema permite "mezclar" lotes. Si se realiza un injerto, se registra que el _Lote C (Producto Final)_ nació de la unión del _Lote A (Pie)_ y el _Lote B (Yema)_, manteniendo la historia completa del origen.

***3. Gestión y Administración***
- Dashboard web para dar de alta Fincas, Sectores y Cepas.
- Gestión de personal (Cosechadores/Cuadrillas) y reportes de salarios acumulados.
- Impresión de etiquetas para identificación física de los bins.

![[flujo.png]]
#### Arquitectura Técnica (Stack Moderno & Ágil)
El sistema se apoya en servicios gestionados para reducir el mantenimiento de infraestructura:
- **Frontend & App:** Desarrollado en **React** (utilizando **Lovable** para aceleración de UI/UX). Funciona como una Web App responsive, priorizando la experiencia móvil de los encargados.
- **Backend & Base de Datos:** **Supabase** (PostgreSQL). Se utiliza como _Backend-as-a-Service_ para gestionar usuarios, base de datos relacional, almacenamiento de fotos y reglas de seguridad en tiempo real.
- **Microservicio de IA:** Un servicio ligero en **Python** que aloja el modelo **YOLOv8**. Recibe la imagen desde Supabase/Frontend, realiza la inferencia (conteo) y devuelve los datos en formato JSON.
---
## 1. Arquitectura de Alto Nivel

El sistema funcionará con una arquitectura **Cliente-Servidor** centralizada en la nube.
- **App Móvil (Operativa):** Para Encargados. Foco en captura de datos, fotos y escaneo de QR. Debe ser _offline-first_ (guardar localmente si se corta internet y subir cuando vuelva), aunque priorizaremos la conexión online.
- **Web Admin (Gestión):** Para Administradores. Alta de fincas, gestión de usuarios, reportes de pagos y visualización del árbol de trazabilidad.
- **Backend (API):** El cerebro que recibe las fotos, gestiona la base de datos y ejecuta la lógica de negocio.
- **Servicio de IA:** Microservicio dedicado a recibir una imagen y devolver `{"count": 105, "boxes": [...]}`.

### Stack Tecnológico
- **Backend:** Python o React.
- **Base de Datos:** PostgreSQL - Supabase. _Necesitamos estructura relacional fuerte para la trazabilidad._
- **App Móvil:** React. _Desarrollando con Lovable_
- **IA/CV:** YOLOv8. _Conteo de objetos densos (estacas) y corre bien en servidores Python._

---

## 2. Modelo de Datos (ERD Simplificado)

Este es el corazón del sistema. Aquí definimos cómo se guardan los datos para lograr la trazabilidad sin volvernos locos.
### Entidades Principales
1. **`Fincas` / `Sectores`**
	- Jerarquía: `Finca` (Los Alamos) -> `Cuadro` (Sector 4) -> `Cepa` (Malbec)
2. **`Personas`**
	- Roles: Admin, Encargado, Cosechador, Cuadrillero.
	- Dato clave: `Saldo_Pendiente` (dinero acumulado por pagar).
3. **`Lotes`**
	- Representa un contenedor físico (Bin) o un grupo lógico.
	- Campos: `ID_Unico`, `Fecha_Creacion`, `Cepa_ID`, `Estado_Actual` (En Frio, En Taller, etc.), `Cantidad_Actual`, `Tipo` (Pie, Yema, Injerto).
4. **`Transacciones_Cosecha`**
	- Registro de cada evento de conteo.
	- Campos: `Foto_URL`, `Cantidad_IA`, `Cantidad_Validada`, `Cosechador_ID`, `Lote_Destino_ID`.
5. **`Traza_Movimientos` (Historial)**
	- Bitácora de qué le pasó al lote.
	- Campos: `Lote_ID`, `Fecha`, `Ubicacion_Anterior`, `Ubicacion_Nueva`, `Usuario_Responsable`.
6. **`Genealogia_Lotes` (Para el Injerto)**
	- Tabla puente para saber de dónde vino un lote nuevo.
	- Campos: `Lote_Padre_ID` (Origen), `Lote_Hijo_ID` (Resultante), `Cantidad_Usada`.
![[UTN-repo/Proyecto/sistema.png]]

---

## 3. Máquina de Estados (Ciclo de Vida del Lote)
En lugar de programar cada proceso biológico, el sistema permitirá mover un lote a través de estas "Ubicaciones/Estados" genéricos:
1. **ORIGEN:** Finca (Estado inicial tras la cosecha).
2. **ALMACENAMIENTO:** Cámara de Frío, Frigorífico, Pozo/Zanja.
3. **PROCESAMIENTO:** Taller de Injerto, Taller de Parafinado, Hidratación.
4. **CAMPO:** Plantación (Cuando vuelve a tierra).
5. **FINAL:** Venta (Sale del sistema) o Baja (Basura).

_Regla de Negocio:_ El usuario simplemente escanea el lote y selecciona "Mover a... \[Lista de Estados]". El sistema registra la fecha y el responsable.

---

## 4. Casos de Uso Clave

### Caso de Uso A: Cosecha y Conteo
1. **Encargado** abre App > Selecciona "Nueva Cosecha".
2. Selecciona Origen: "Finca A - Cuadro 1 (Malbec)".
3. Escanea QR del **Cosechador** (o lo busca en lista).
4. Toma **Foto** a los atados.
5. **Sistema (IA):** Procesa y muestra la foto con cuadritos verdes sobre cada estaca. Muestra: "Conteo: 102".
6. **Encargado:** Verifica. Si ve un error, toca la pantalla para agregar/quitar marcas. Confirma "100".
7. **Sistema:**
	- Suma 100 a la cuenta corriente del Cosechador.
	- Suma 100 al "Bin Abierto" actual de esa Finca.
### Caso de Uso B: Cierre de Lote (Etiquetado)
1. El Bin se llena.
2. **Encargado** selecciona "Cerrar Lote".
3. **Sistema:** Genera ID único (ej: `L-2025-MB-884`) y manda a imprimir etiqueta (o muestra datos para escribir en tarjeta).
4. El stock de ese lote queda "Disponible" para mover.
### Caso de Uso C: Transformación (Injerto/Mezcla)
1. En el Taller, el operario selecciona "Nuevo Proceso: Injerto".
2. Escanea **Lote Origen 1** (Pie).
3. Escanea **Lote Origen 2** (Yema).
4. Indica cuántas unidades usó de cada uno.
5. El sistema crea un **Nuevo Lote Destino** (Planta Injertada).
6. El sistema vincula en `Genealogia_Lotes`: El Lote Nuevo es hijo de Origen 1 y Origen 2.
![[acciones.png]]
