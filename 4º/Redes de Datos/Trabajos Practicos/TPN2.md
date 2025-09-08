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
 8. Explicar y graficar las tramas Ethernet y IEEE 802.3.  Qué diferencias
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
- **Coaxial (10Base5, 10Base2):** primeras versiones de Ethernet. Hoy obsoleto.
- **Par trenzado (UTP/STP, 10/100/1000Base-T):** el más común, económico y flexible.
- **Fibra óptica (100Base-FX, 1000Base-LX, 10GBase):** largas distancias, alta velocidad e inmunidad al ruido.

### 9. Longitud mínima y máxima de las tramas
- **Longitud mínima (64 bytes):** necesaria para garantizar que, en CSMA/CD, una colisión pueda detectarse antes de que termine la transmisión.
- **Longitud máxima (1518 bytes):** evita que una sola estación monopolice el medio por demasiado tiempo, mejora la equidad y limita la latencia.

### 10. 