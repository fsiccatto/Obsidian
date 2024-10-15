
# Producto
Es el resultado de un proceso, ya sea un producto final o intermedio.

**Ejemplo fuera del software**: al hacer una torta, el producto intermedio sería el bizcochuelo y el producto final la torta lista.

En software, los productos pueden incluir programas, formularios, documentos y datos. El producto final puede ser un software completo, pero a lo largo del proceso se generan otros productos intermedios como documentación y formularios.

# Proceso
Es una serie de pasos a seguir para construir un sistema o producto. Sirve como marco de trabajo que aporta organización, control y estabilidad.

Es fundamental para lograr software de alta calidad, y es gestionado por la ingeniería de software. El proceso permite controlar los tiempos y productos intermedios para asegurar el cumplimiento de objetivos.

# Sistemas de Información
Un sistema de información opera sobre una colección de datos estructurados que recopilan, elaboran y distribuyen información para apoyar la gestión, toma de decisiones y control de una empresa.

Están alineados con la estrategia de negocio de la empresa y apoyan las funciones administrativas principales.


## Ingeniería de Software: Capas y Fases

### Capas de la Ingeniería de Software
Estas capas representan la estructura sobre la cual se construye el proceso de desarrollo de software. Son fundamentales para garantizar un enfoque disciplinado y organizado.

- **Enfoque de Calidad**: Es la base de todo el proceso, asegurando que el software cumpla con estándares de calidad.
- **Proceso**: Mantiene unidas las capas y establece el marco de trabajo.
- **Métodos**: Definen cómo construir el software técnicamente (análisis, diseño, pruebas, etc.).
- **Herramientas**: Dan soporte al proceso, automatizando tareas y actividades.

![[imgs/13.png|center|230]]
### Fases del Proceso de la Ingeniería de Software
El proceso de desarrollo de software se divide en tres grandes fases, cada una de las cuales tiene objetivos específicos.

- **Definición (el "qué")**: Se determinan requisitos, funciones, rendimiento, y comportamiento del sistema.
- **Desarrollo (el "cómo")**: Se diseñan estructuras de datos, se implementan funciones y se realizan pruebas.
- **Mantenimiento (el "cambio")**: Se corrigen errores, se adapta el software a nuevos entornos, y se realizan mejoras.

Las **actividades protectoras** surgen una vez que el sistema está en producción, lo que lleva a un ciclo de mejora y actualización constante.

# Ciclo de Vida del Desarrollo de Software (SDLC)
El ciclo de vida de desarrollo de software guía el proceso desde la recolección de requisitos hasta su mantenimiento. Las fases incluyen análisis, diseño, implementación, pruebas y despliegue.

## Ciclo de Vida Clásico (Secuencial o Cascada)
Este modelo se caracteriza por la secuencialidad y linealidad de las fases. Las tareas se ejecutan una después de la otra, sin posibilidad de regresar a fases anteriores.

### Fases:
1. Especificación de Requisitos.
2. Análisis.
3. Diseño.
4. Implementación (Codificación).
5. Pruebas y Mantenimiento.

- **Implantación Ascendente**: Las pruebas se realizan primero a nivel de módulos, luego subsistemas y finalmente al sistema completo.
- **Progresión Secuencial**: Cada fase avanza de manera rígida y sin retrocesos.

## Ciclo de Vida Estructurado
Permite realizar tareas en paralelo, estableciendo vínculos entre actividades y diferentes áreas (usuarios, administración, operaciones). Incluye nuevas actividades como la **conversión de bases de datos, generación de pruebas de aceptación, y control de calidad.**

- **Implantación Descendente**: Se realizan primero pruebas del sistema completo, luego del subsistema y finalmente de los módulos.
- **Flexibilidad para Retroceder**: A diferencia del ciclo clásico, permite regresar a fases anteriores si es necesario.

## Desarrollo Rápido de Aplicaciones (DRA)
Modelo lineal secuencial que enfatiza un período de desarrollo corto (60-90 días). Permite un desarrollo acelerado y más flexible.

- **Actividades comunes**: Modelado de gestión, modelado de datos, modelado de procesos, modelado de aplicaciones, pruebas, y entrega.

# Modelos Evolutivos
Los modelos evolutivos permiten desarrollar el software de manera incremental y adaptativa dividiendo el proyecto en versiones pequeñas que se mejoran gradualmente. En cada iteración, se incorpora retroalimentación del cliente, lo que permite ajustes continuos.

### Características:
- **Iterativos**: Se repiten fases como análisis, diseño, codificación y prueba.
- **Interactivos**: Se interactúa con el cliente para mostrar avances y obtener feedback.
- **Lineal Secuenciales**: Las tareas se realizan de manera secuencial dentro de cada iteración.
- **Entregan versiones más completas:** Cada iteración mejora el producto con nuevas funcionalidades
## Modelo Incremental
Se construye el sistema en partes, donde cada incremento agrega funcionalidades al producto esencial inicial. Cada incremento es funcional y entregable.

**Ejemplo**: Sistema académico donde en un primer incremento se implementa la inscripción de alumnos.
![[imgs/14.png|center]]
## Modelo en Espiral
Es un modelo evolutivo con énfasis en la gestión de riesgos. No entrega un producto funcional hasta completar varias vueltas de la espiral. Se evalúa el producto y los riesgos en cada ciclo.
![[imgs/15.png|center]]
## Prototipos
Un prototipo es una versión preliminar de un sistema que busca representar rápidamente ciertas características del software. 

### Tipos de Prototipos:
1. **Prototipos de Requisitos.** Muestran las pantallas o informes para que el cliente vea cómo será la interfaz y lo que recibirá del sistema.
2. **Prototipos de Análisis**. Ayudan a definir la arquitectura general del sistema para asegurar que se entienda cómo funcionará.
3. **Prototipos de Diseño**. Profundizan en cómo se implementará técnicamente el sistema, destacando aspectos clave de la ingeniería de software.
4. **Prototipos Verticales.** Abordan tanto el problema como la solución.
5. **Prototipos de Factibilidad**. Sirven para verificar si es viable llevar a cabo el proyecto propuesto.

El riesgo de los prototipos es que los clientes pueden confundirlos con el producto final.

# Reutilización de Componentes
La reutilización implica aprovechar componentes de software previamente desarrollados para ahorrar tiempo y recursos. Existen dos enfoques principales:
### Enfoques:
- **Bajo nivel**: Reutilización dentro del mismo sistema aplicando técnicas como la herencia.
- **Alto nivel**: Reutilización entre sistemas mediante bibliotecas o paquete de componentes

# Herramientas de Desarrollo
Existen varias herramientas que facilitan el desarrollo de software, como editores de texto, compiladores, depuradores y administradores de proyectos.

# Modelos de Procesos

## Procesos Dirigidos por un Plan
Son más estructurados y se basan en una planificación detallada.

## Procesos Ágiles
Son más flexibles y adaptables a los cambios en los requerimientos del cliente. Permiten iteraciones rápidas con entregas incrementales.

# Proceso Unificado (RUP)
Es un modelo evolutivo caracterizado por ser iterativo, incremental, y dirigido por casos de uso.

Sus características son: 
- **Iterativo e Incremental:** Repite ciclos en los que se entregan versiones incrementales del software, es decir, versiones cada vez más completas a lo largo del proceso. 
- **Dirigido por Casos de Uso:** Cada etapa del desarrollo se basa en casos de uso que guían la creación de los distintos modelos (análisis, diseño, pruebas, etc.). 
- **Centrado en la Arquitectura:** La arquitectura del sistema se establece como base y guía para el diseño del software, asegurando que sea estructuralmente sólido y escalable
### Fases:
1. **Inicio**: Se definen los objetivos y el alcance del proyecto.
2. **Elaboración**: Se diseña la arquitectura del sistema.
3. **Construcción**: Se implementan las funcionalidades a través de iteraciones.
4. **Transición**: Se entrega una versión funcional del software.

### Flujos de Trabajo:
- Requerimientos.
- Análisis.
- Diseño.
- Implementación.
- Pruebas.

El **Proceso Unificado** permite la creación de un software más robusto y flexible, ya que cada iteración entrega un producto más completo, validado continuamente en conjunto con el cliente