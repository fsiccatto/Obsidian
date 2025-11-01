# Captura y análisis de segmentos TCP y UDP
## Análisis de los campos TCP
Abri un servidor con la siguiente URL [192.168.54.139:8080](http://192.168.54.139:8080/) utilizando la aplicación para android *Simple HTTP Server*.
Captura de Wireshark:
![[wireshark.png]]
En la captura se puede observar:
- Source `192.168.54.174` (la PC que funciona como cliente HTTP)
- Destination `192.168.54.139` (el celular que funciona como servidor)
- Protocolo HTTP o TCP
- Información `GET / HTTP/1.1`, `200 OK`, `ACK`, `SYN`.

Captura del servidor:
![[servidor.jpg | 200]]

---

1. Observe y responda, cómo se identifica el primer segmento de una conexión TCP? 
El primer segmento de una conexión TCP se identifica por el bit `SYN` (*Synchronize*) establecido en 1.  
Esto marca el inicio del *three-way handshake* que usa TCP para crear una conexión confiable.
- **Cliente → Servidor:** envía un segmento con SYN = 1.
- **Servidor → Cliente:** responde con SYN = 1 y ACK = 1.
- **Cliente → Servidor:** envía ACK = 1.
Este intercambio asegura que ambas partes están listas para transmitir datos.

2. Grafique un segmento TCP y detalle la información que brinda cada campo.

| Campo                                     | Tamaño (bits) | Descripción                                                                                                                       |
| ----------------------------------------- | ------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| **Puerto de origen**                      | 16            | Identifica el puerto del proceso emisor (por ej., un puerto efímero en el cliente).                                               |
| **Puerto de destino**                     | 16            | Identifica el puerto del proceso receptor (por ej., 80 para HTTP).                                                                |
| **Número de secuencia**                   | 32            | Indica el número del primer byte de datos enviados en este segmento. En el primer SYN se elige un número inicial aleatorio (ISN). |
| **Número de acuse de recibo (ACK)**       | 32            | Indica el número del siguiente byte que el emisor espera recibir. Solo válido si el bit ACK está en 1.                            |
| **Longitud del encabezado (Data Offset)** | 4             | Indica el tamaño del encabezado TCP (normalmente 20 bytes si no hay opciones).                                                    |
| **Bits de control**                       | 6 (o más)     | URG, ACK, PSH, RST, SYN, FIN. Determinan el tipo de segmento.                                                                     |
| **Tamaño de la ventana (Window Size)**    | 16            | Control de flujo: indica cuántos bytes puede aceptar el receptor.                                                                 |
| **Checksum**                              | 16            | Verifica la integridad del segmento.                                                                                              |
| **Urgent Pointer**                        | 16            | Indica si hay datos urgentes (poco usado).                                                                                        |
| **Opciones**                              | Variable      | Por ejemplo, “Window Scale” o “Timestamp”.                                                                                        |
| **Datos (Payload)**                       | Variable      | Contenido real (por ej., una petición HTTP).                                                                                      |

3. Ahora relacione este gráfico con la información capturada con Wireshark. 
![[wireshark2.png]]

4. Utilice la captura Wireshark del inicio de la primera sesión TCP (bit SYN fijado en 1) para completar la información acerca del encabezado TCP:

-  Desde el cliente hacia el servidor (SYN = 1):

| Campo                         | Valor          |
| ----------------------------- | -------------- |
| **Dirección IP de origen**    | 192.168.54.174 |
| **Dirección IP destino**      | 192.168.54.139 |
| **Puerto de origen**          | 65335          |
| **Puerto de destino**         | 8080           |
| **Número de secuencia**       | 0              |
| **Número de acuse de recibo** | 0              |
| **Longitud del encabezado**   | 32 bytes       |
| **Tamaño de la ventana**      | 65535 bytes    |
- Desde el cliente al servidor (sólo los bits SYN y ACK se fijan en 1):

| Campo                         | Valor          |
| ----------------------------- | -------------- |
| **Dirección IP de origen**    | 192.168.54.174 |
| **Dirección IP destino**      | 192.168.54.1   |
| **Puerto de origen**          | 65535          |
| **Puerto de destino**         | 8080           |
| **Número de secuencia**       | 0              |
| **Número de acuse de recibo** | 1              |
| **Longitud del encabezado**   | 32 bytes       |
| **Tamaño de la ventana**      | 65535 bytes    |

- Desde el cliente al servidor (sólo el bit ACK se fija en 1):

| Campo                         | Valor          |
| ----------------------------- | -------------- |
| **Dirección IP de origen**    | 192.168.54.174 |
| **Dirección IP destino**      | 192.168.54.1   |
| **Puerto de origen**          | 65535          |
| **Puerto de destino**         | 8080           |
| **Número de secuencia**       | 1              |
| **Número de acuse de recibo** | 1              |
| **Longitud del encabezado**   | 20 bytes       |
| **Tamaño de la ventana**      | 65280 bytes    |

## Análisis de los campos UDP
![[wiereshark udp.png]]
- Source: `192.168.54.174`  
- Destination: `142.251.129.4 ` 
- Protocol: UDP  
- Source Port: `59293`  
- Destination Port: `443` 
- Length: `519` bytes

3. Grafique un segmento UDP y detalle la información que brinda cada campo
|<---------------------- 32 bits ---------------------->|
|     Puerto origen (16)           |   Puerto destino (16)              |
|----------------------------------------------------------|
|       Longitud (16)                  |                Checksum (16)       |
|----------------------------------------------------------|
|                                  Datos (payload)                                    |

|Campo|Tamaño (bits)|Descripción|
|---|---|---|
|**Puerto de origen**|16|Identifica el proceso que envía los datos (en este caso, 59293 del cliente).|
|**Puerto de destino**|16|Identifica el proceso receptor (443 en el servidor de Google).|
|**Longitud del mensaje UDP**|16|Tamaño total del datagrama (encabezado + datos).|
|**Checksum**|16|Verifica errores en el encabezado o los datos.|
|**Datos (payload)**|Variable|Contenido transmitido (por ejemplo, tráfico HTTP/3).|
4. Relación con Wireshark
![[wireshark udp 2.png]]
5. Primer datagrama UDP

| Campo                           | Valor                            |
| ------------------------------- | -------------------------------- |
| **Dirección IP de origen**      | 192.168.54.174                   |
| **Dirección IP destino**        | 142.251.129.4                    |
| **Número de puerto de origen**  | 59293                            |
| **Número de puerto de destino** | 443                              |
| **Longitud de mensaje UDP**     | 519 bytes                        |
| **Checksum de UDP**             | Checksum: `0x72b6` \[unverified] |
6. Primer paquete de respuesta UDP (del servidor) 
![[wireshark udp 3.png]]

| Campo                           | Valor (ejemplo)                  |
| ------------------------------- | -------------------------------- |
| **Dirección IP de origen**      | 142.251.129.4                    |
| **Dirección IP destino**        | 192.168.54.174                   |
| **Número de puerto de origen**  | 443                              |
| **Número de puerto de destino** | 59293                            |
| **Longitud de mensaje UDP**     | 43 bytes                         |
| **Checksum de UDP**             | Checksum: `0x16dc` \[unverified] |
7. Ping a google
![[ping google.png]]
En wireshark con `imcp.type == 8` (request)
![[wireshark imcp.png]]

| Campo                      | Valor            |
| -------------------------- | ---------------- |
| **Dirección IP de origen** | 192.168.54.174   |
| **Dirección IP destino**   | 8.8.8.8          |
| **Type**                   | 8 (Echo request) |
| **Code**                   | 0                |
| **Checksum**               | 0xXXXX           |
| **Identifier**             | 0x0001           |
| **Sequence Number**        | 64               |



y con `imcp == 0` (reply)
![[wireshark imcp 2.png]]

| Campo                      | Valor          |
| -------------------------- | -------------- |
| **Dirección IP de origen** | 8.8.8.8        |
| **Dirección IP destino**   | 192.168.54.174 |
| **Type**                   | 0 (Echo reply) |
| **Code**                   | 0              |
| **Checksum**               | 0x5b3e         |
| **Identifier**             | 0x0001         |
| **Sequence Number**        | 64             |
| **TTL**                    | 117            |

El protocolo ICMP se utiliza para enviar mensajes de control y diagnóstico, como las solicitudes y respuestas de eco que se usan en el comando _ping_.
En la captura, se observa el intercambio entre el host local (192.168.54.174) y el servidor 8.8.8.8.  
Cada solicitud ICMP (Type 8) recibe su correspondiente respuesta (Type 0), confirmando la conectividad entre ambos equipos.  
Los campos _Identifier_ y _Sequence Number_ permiten asociar cada solicitud con su respuesta, y el campo _TTL_ indica el número de saltos restantes antes de que el paquete sea descartado.