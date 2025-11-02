1. ¿Cuáles son las propiedades deseables en una comunicación segura?
   Las propiedades básicas deseables incluyen:
- **Confidencialidad**: que solo usuarios autorizados puedan acceder a la información.
- **Integridad**: que la información no sea modificada sin autorización.
- **Disponibilidad**: los recusos están accesibles cuando se necesitan
- **Autenticación**: confirmar la identidad de las partes que se comunican.
- **No repudio**: que una parte no pueda negar haber realizado una acción o enviado un mensaje.
    ​
2. Indicar los principios de la criptografía. Explicar la criptografía simétrica y asimétrica.
Principios de la criptografía: Confidencialidad, Integridad, Autenticación y No repudio.
**Criptografía simétrica**:
Usa la misma clave para cifrar y descifrar. Ejemplo: AES, DES.
- Ventaja: rápida.
- Desventaja: distribución segura de la clave.

**Criptografía asimétrica**:
Usa par de claves: pública (cifrar) y privada (descifrar). Ejemplo: RSA, ECC.
- Ventaja: evita compartir claves secretas.
- Desventaja: más lenta computacionalmente.

3. ¿Qué son y qué función cumplen las funciones hash?
Las funciones hash son algoritmos que transforman datos de tamaño variable en una cadena de longitud fija, única para esos datos. Su función principal es verificar la integridad de la información, permitiendo detectar cualquier cambio incluso mínimo en los datos originales.

4. Explicar la funcionalidad de la firma digital.
La firma digital usa criptografía asimétrica para asegurar la autenticidad e integridad de un mensaje o documento. El remitente firma digitalmente el mensaje con su clave privada, y el receptor verifica la firma con la clave pública del remitente, garantizando que el mensaje es auténtico y no ha sido alterado.

5. ¿Qué es un certificado de clave pública?
Es un documento electrónico que vincula una clave pública con la identidad de su propietario, emitido y firmado por una Autoridad de Certificación (CA). Proporciona confianza en la autenticidad de la clave pública.

6. Graficar cómo se verifica un mensaje firmado.
   
Emisor                      Receptor
-------                     --------
Mensaje ----> Hash ---> Cifrado con clave privada (Firma)
                   ↓
                Firma digital
-----------------------------------------------> Mensaje + Firma
                      ↓
                Hash(Mensaje recibido)
                Descifrar Firma (clave pública)
                Comparar ambos hashes

7. ¿Qué función cumple la Autoridad de Certificación CA?
La CA autentica la identidad de las entidades y emite certificados digitales que vinculan la identidad con una clave pública, facilitando la confianza en las comunicaciones.

8. ¿Cómo pueden autenticarse los puntos terminales?
Se realiza mediante mecanismos como certificados digitales, protocolos de autenticación mutua, uso de contraseñas, tokens o biometría para verificar la identidad de los dispositivos o usuarios involucrados en la comunicación.

9. Explicar los mecanismos para dar seguridad al correo electrónico.
Se utilizan métodos como cifrado (PGP, S/MIME), firmas digitales y protocolos seguros (TLS en SMTP) para garantizar confidencialidad, integridad y autenticación del correo electrónico.

10. ¿Cómo podemos mejorar los servicios de seguridad de TCP?
Se incorporan protocolos complementarios como TLS/SSL para cifrar las comunicaciones TCP y autenticación, evitando interceptaciones y ataques.

11. Explicar el funcionamiento de SSL.
SSL (y su sucesor TLS) proporciona seguridad en la capa de transporte usando cifrado simétrico y asimétrico para establecer canales seguros entre clientes y servidores, garantizando confidencialidad, integridad y autenticación.
- **Cifrado de datos:** comunicación segura con claves simétricas derivadas.
- **Negociación de algoritmos de cifrado.*
- **Handshake:** intercambio de claves y autenticación del servidor (y opcional del cliente).

12. ¿Qué servicios ofrece IPSec? ¿Qué ventajas tienen las redes privadas virtuales?
IPSec ofrece cifrado, autenticación y protección de integridad en el nivel IP, asegurando el tráfico de red. Aseguran autenticación, integridad y cifrado.
Las VPN crean redes privadas seguras sobre redes públicas, protegiendo comunicaciones y extendiendo redes corporativas. Son de acceso remoto seguro y oculta la red de internet.

13. ¿Qué mecanismos existen para segurizar las redes inalámbricas?
Se aplican mecanismos como WPA3 para cifrado robusto, autenticación mediante certificados o contraseñas seguras, y detección de intrusos para proteger la red inalámbrica.
- **WPA3 / WPA2:** cifrado robusto (AES-CCMP).
- **802.1X / EAP:** autenticación basada en servidor.
- **VPN sobre Wi-Fi.**
- Filtrado MAC y ocultamiento SSID (complementarios, no suficientes).

14. Explicar el funcionamiento de los firewalls y de los sistemas de detección de intrusos. Graficar
Un **firewall** es un dispositivo de seguridad de red que actúa como una **barrera** entre una red interna de confianza (como la red de tu oficina o tu casa) y redes externas no confiables (como Internet).
El trabajo principal es filtrar el tráfico de red entrante y saliente basándose en un conjunto de reglas de seguridad predefinidas.

El **Sistema de detección de Instrusos** (*IDS*) no bloquea el tráfico. Su trabajo es monitorear la red en busca de actividades sospechosas o maliciosas y generar alertas cuando las detecta.

INTERNET ---> Firewall ---> IDS ---> Red interna
      | Bloquea tráfico no permitido      |
      | IDS detecta y alerta intrusiones |
