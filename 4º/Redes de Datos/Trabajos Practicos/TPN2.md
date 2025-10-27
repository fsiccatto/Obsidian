# La subcapa de control de acceso al medio
## Cuestionario
 1. ¿En qué consiste la asignación estática de canal en LANs y MANs?
 ¿Cómo puede medirse en desempeño?  
2. ¿En qué consiste la asignación dinámica de canal en LANs y MANs?  
3. Explicar las características del protocolo ALOHA en cada una de sus
 variantes.
 4. Explicar las características del protocolo CSMA persistente y no persistente.
 5. Explicar las características del protocolo CSMA con detección de colisiones.
 6. ¿Qué protocolos están disponibles para las redes LAN inalámbricas?
 7. Explicar y graficar los distintos tipos de cableados de las redes Ethernet.
 8. Explicar y graficar las tramas Ethernet y IEEE 802.3. ¿Qué diferencias
 tienen?
 9. ¿Porqué las tramas deben tener una longitud máxima y una mínima?
 10. ¿Cómo medimos el desempeño de una red Ethernet?
 11. ¿Qué ventajas tiene una red Ethernet conmutada?
 12. Realizar un estudio comparativo entre redes FastEthernet y
 GigabitEthernet.

--- 

## Respuestas
### 1. Asignación estática de canal en LANs y MANs
La asignación estática de canal en LANs y MANs consiste en la preasignación fija de canales o porciones del medio de transmisión a nodos o estaciones específicas, sin cambios dinámicos durante la operación. Esto quiere decir que cada dispositivo tiene un canala asignado previamente y no compite por el acceso al canal en tiempo real.
Es común en redes donde la carga de tráfico es predecible o que tienen requierimientos estrictos de calidad de servicio, evitando colisiones y reduciendo la sobrecarga del protocolo.
#### Desempeño
Respecto a la **medición del desempeño**, el desempeño de la asignación estática de canal puede medirse en términos de:
- **Ancho de banda efectivo utilizado** (*throughput*), evaluando qué porcentaje del tiempo está efectivamente transmitiendo sin colisiones.
- **Retraso o latencia** en la transmisión, que suele ser bajo si el canal está dedicado.
- **Utilización del canal**, que en sistemas estáticos puede ser baja si un canal asignado está infrautilizado.
- **Tasa de error en la transmisión** en caso de interferencias o ruidos.

### 2. Asignación dinámica de canal en LANs y MANs
La asignación dinámica de canal en LANs y MANs consiste en que los canales o porciones del medio de transmisión no están asignados de manera fija, sino que se asignan según demanda y necesidad en tiempo real a los nodos o estaciones. Esto permite una utilización más flexible y eficiente del espectro o medio compartido, adaptándose a la variabilidad del tráfico.
La asignación dinámica puede involucrar mecanismos de arbitraje y coordinación para evitar colisiones y garantizar el acceso justo y eficiente al canal.

### 3. Características del protocolo ALOHA
El protocolo ALOHA es un método de acceso al medio para redes que se caracteriza por permitir a los nodos transmitir datos cuando lo desean, con mecanismos para manejar colisiones. Tiene dos variantes principales que presentan diferencias en su funcionamiento y eficiencia:

1. **ALOHA Puro:**
    - Cada estación transmite en cualquier momento sin coordinación previa.
    - Si ocurre una colisión (dos estaciones transmiten al mismo tiempo), ambos paquetes se pierden.
    - Las estaciones retransmiten después de un intervalo de tiempo aleatorio.
    - Es fácil de implementar pero tiene baja eficiencia debido a la alta probabilidad de colisiones.
    - La eficiencia máxima teórica es alrededor del 18%.
        
2. **ALOHA Ranurado:**
    - El tiempo se divide en intervalos o ranuras (*slots*) iguales.
    - Las estaciones solo pueden transmitir al inicio de una ranura.
    - Esto reduce la probabilidad de colisiones a la mitad comparado con ALOHA puro.
    - La eficiencia máxima teórica mejora hasta cerca del 37%.
    - Requiere sincronización entre estaciones para respetar las ranuras.

Ambas variantes se usan en diferentes contextos según la necesidad de simplicidad o eficiencia y son la base histórica para protocolos modernos de acceso al medio en redes como Ethernet, Wi-Fi y redes satelitales.

### 4. Características del protocolo CSMA persistente y no persistente.
CSMA o Acceso Múltiple por Detección de Portadora es un protocolo que permite a múltiples dispositivos compartir un mismo medio de transmisión, como una red cableada o inalámbrica, para enviar datos de manera ordenada.

- **CSMA persistente (1-persistente):**  
    Cuando la estación quiere transmitir, escucha el canal.
    - Si está **libre**, transmite de inmediato.
    - Si está **ocupado**, espera hasta que se libere y transmite en cuanto lo detecta.
    - Desventaja: genera **colisiones** cuando varias estaciones esperan y transmiten al mismo tiempo.
    
- **CSMA no persistente:**  
    La estación escucha el canal.
    - Si está libre, transmite.
    - Si está ocupado, espera un tiempo **aleatorio** antes de volver a escuchar.
    - Ventaja: **menos colisiones**, pero menor aprovechamiento del canal.

### 5. CSMA con detección de colisiones (CSMA/CD)
Si dos dispositivos transmiten al mismo tiempo, ocurre una colisión. CSMA/CD permite que los dispositivos detecten esta colisión, detengan la transmisión y esperen un tiempo aleatorio antes de reintentar.

### 6. Protocolos disponibles para las redes LAN inalámbricas
El protocolo de acceso al medio que utilizan es **CSMA/CA** (Acceso Múltiple por Detección de Portadora con Prevención de Colisiones).
Los estándares más comunes de esta familia (que definen las velocidades y frecuencias) son:
- **802.11b:** (Hasta 11 Mbps, 2.4 GHz)
- **802.11g:** (Hasta 54 Mbps, 2.4 GHz)
- **802.11n (Wi-Fi 4):** (Hasta 600 Mbps, 2.4/5 GHz, introduce MIMO)
- **802.11ac (Wi-Fi 5):** (Hasta ~6.9 Gbps, 5 GHz)
- **802.11ax (Wi-Fi 6/6E):** (Hasta ~9.6 Gbps, 2.4/5/6 GHz, enfocado en eficiencia y alta densidad de dispositivos)
### 7. Explicar y graficar los distintos tipos de cableados de las redes Ethernet.
Históricamente, Ethernet ha usado tres tipos principales de cableado, asociados a distintas topologías:
1. **Cable Coaxial (Topología de Bus):**
    - Usado en las primeras redes (10Base5 "Thicknet" y 10Base2 "Thinnet").
    - Velocidad típica 10 Mbps.
    - Todos los dispositivos se conectaban a un único cable compartido (bus).
    - Requería terminadores en ambos extremos del cable para evitar reflexiones de señal, muy rígido y un solo cable compartido.
    ![[Pasted image 20251026223735.jpg | 200]]
2. **Par Trenzado (UTP/STP) (Topología de Estrella):**
    - Es el estándar actual (10Base-T, 100Base-TX, 1000Base-T, 10GBase-T).
    - Velocidad de 10 Mbps hasta 10 Gbps.
    - Tipos comunes
	    - UTP
	    - STP
    - Cada dispositivo se conecta con su propio cable a un dispositivo central (hub o, más comúnmente, un **switch**).
    - Flexible, económico y fácil de instalar. Permite distancias de hasta 100m por enlace.
    - Usa conectores RJ45.
    ![[Pasted image 20251026223756.jpg | 200]]
3. **Fibra Óptica (Topología de Estrella o Punto a Punto):**
    - Usado para alta velocidad (100Base-FX, 1000Base-SX/LX, 10/40/100 GBase).
	    - Monomodo: un solo haz de luz, larga distancia (decenas de km)
	    - Multimodo: varios haces, corta distancia (hasta 2km)
    - Ideal para distancias largas (varios kilómetros) y entornos con alta interferencia electromagnética.
    - Se usa comúnmente para _backbones_ (enlaces troncales) entre switches o para conectar edificios.
    ![[Pasted image 20251026223834.jpg | 200]]
### 8. Explicar y graficar las tramas Ethernet y IEEE 802.3. ¿Qué diferencias tienen?
#### Estructura de la Trama
La trama se compone de los siguientes campos:
- **Preámbulo (7 bytes):** Sincronización (alterna 1s y 0s).
- **SFD (1 byte):** Delimitador de inicio de trama (10101011).
- **MAC Destino (6 bytes):** Dirección física del receptor.
- **MAC Origen (6 bytes):** Dirección física del emisor.
- **Tipo/Longitud (2 bytes):** **¡Aquí está la diferencia clave!**
- **Datos (46 a 1500 bytes):** El _payload_ (paquete IP, etc.).
- **FCS (4 bytes):** Secuencia de verificación de trama (CRC para detectar errores).
#### Diferencias (Campo Tipo/Longitud)
1. **Trama Ethernet II (o DIX):**
    - Este formato es el estándar usado hoy.
    - El campo de 2 bytes se usa como **Tipo (Type)**.
    - Indica qué protocolo de capa superior está contenido en los datos (ej. `0x0800` para IPv4, `0x0806` para ARP).
    - Cualquier valor en este campo **mayor a 1536** (0x0600) se interpreta como un "Tipo".
    ![[Pasted image 20251027091357.png]]
    
2. **Trama IEEE 802.3 (Original):**
    - En el estándar original, este campo se usaba como **Longitud (Length)**.
    - Indicaba el número de bytes en el campo de datos.
    - Cualquier valor **igual o menor a 1500** (0x05DC) se interpreta como "Longitud".
    - Para saber el protocolo de capa superior, 802.3 requería usar un encabezado extra (LLC 802.2) dentro del campo de datos, lo que añade complejidad.
	![[Pasted image 20251027091249.png]]
En resumen, la principal diferencia entre ambos formatos radica en el campo Tipo/Longitud: Ethernet II usa este campo para identificar el protocolo de capa superior, mientras que IEEE 802.3 lo usa para indicar la longitud y requiere un encabezado adicional LLC/SNAP. Por simplicidad y compatibilidad, Ethernet II es el formato más utilizado actualmente.

### 9. Longitud mínima y máxima de las tramas
- **Longitud mínima (64 bytes):** necesaria para garantizar que, en CSMA/CD, una colisión pueda detectarse antes de que termine la transmisión.
- **Longitud máxima (1518 bytes):** evita que una sola estación monopolice el medio por demasiado tiempo, mejora la equidad y limita la latencia.

### 10. Medición del desempeño en una red Ethernet
El desempeño de una red Ethernet puede medirse principalmente mediante los siguientes indicadores:
- **Throughput (ancho de banda efectivo):** cantidad de datos útiles transmitidos por unidad de tiempo, considerando la pérdida por colisiones y retransmisiones.
- **Latencia:** tiempo que tarda un paquete en viajar desde el emisor al receptor.
- **Tasa de colisiones:** número de colisiones que ocurren en la red durante un período determinado.
- **Tasa de errores:** porcentaje de tramas erróneas que deben ser retransmitidas.
- **Utilización del canal:** porcentaje del tiempo en que el medio está siendo utilizado para transmisión efectiva.

### 11. Ventajas de una red Ethernet conmutada
- **Reducción de colisiones:** Al conectar cada estación a un puerto exclusivo del switch, cada enlace opera en modo dedicado, evitando colisiones.
- **Mayor rendimiento:** Al eliminar la competencia por el medio, el throughput es casi máximo teórico para cada enlace.
- **Segmentación eficiente:** Los switches pueden segmentar la red en dominios de colisión más pequeños, mejorando el desempeño.
- **Soporte para full-duplex:** Permite transmisión y recepción simultánea sin colisiones.
- **Escalabilidad:** Facilita agregar más nodos sin degradación significativa de rendimiento.
- **Mejora la seguridad:** Permite controlar y filtrar el tráfico entre puertos.

### 12. Estudio comparativo entre FastEthernet y GigabitEthernet

|Característica|FastEthernet (FE)|GigabitEthernet (GE)|
|---|---|---|
|Velocidad|100 Mbps|1 Gbps (1000 Mbps)|
|Medios de transmisión|Par trenzado (Cat5) y fibra óptica|Par trenzado (Cat5e/Cat6), fibra óptica|
|Distancia máxima|Hasta 100 m (UTP)|Hasta 100 m (UTP Cat5e/Cat6), más en fibra óptica|
|Costos|Menor costo|Generalmente mayor por velocidad y componentes|
|Uso típico|Redes de área local estándar|Redes que requieren mayor ancho de banda, centros de datos|
|Compatibilidad|Compatible con Ethernet 10Base-T|Compatible con FastEthernet y Ethernet 10Base-T mediante auto-negociación|
|Soporte full-duplex|Sí|Sí|
|Consumo energético|Bajo|Relativamente mayor|
