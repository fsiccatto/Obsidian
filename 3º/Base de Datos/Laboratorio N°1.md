# Actividad de Laboratorio N°1
## Instalación y configuración de Motores de Bases de Datos en Docker con Ubuntu y Oracle Linux
### 1. Entorno Teórico
1. Investigar y explicar sintéticamente Clasificación de DBMS.
- **Según el modelo de datos**
Los DBMS se clasifican por la forma en que organizan la información. El modelo relacional (el más difundido) estructura los datos en tablas con filas y columnas vinculadas mediante claves. El modelo jerárquico organiza los datos en una estructura de árbol con relaciones padre-hijo. El modelo de red extiende el jerárquico permitiendo que un nodo hijo tenga múltiples padres. El modelo orientado a objetos almacena los datos como objetos, integrando conceptos de la programación orientada a objetos. Los modelos NoSQL (documental, clave-valor, columnar y grafos) surgieron para manejar datos no estructurados y alta escalabilidad.
- **Según la cantidad de usuarios**
Un DBMS monousuario permite que solo un usuario acceda a la base de datos a la vez (ej.: Microsoft Access en uso individual). Un DBMS multiusuario soporta acceso concurrente de múltiples usuarios, gestionando bloqueos y transacciones para mantener la consistencia (ej.: Oracle, MySQL, SQL Server).
- **Según la distribución geográfica**
Un DBMS centralizado almacena todos los datos en un único servidor o ubicación. Un DBMS distribuido reparte los datos en múltiples nodos geográficamente dispersos, conectados por una red, brindando mayor disponibilidad, tolerancia a fallos y rendimiento local. Los datos pueden estar replicados o fragmentados entre los nodos.

2. Describir brevemente tres DBMS comerciales

| **DBMS**            | **Desarrollador**             | **Descripción**                                                                                                                                                                                                                                                 |
| ------------------- | ----------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Oracle Database** | Oracle Corp.                  | DBMS relacional líder en entornos empresariales. Soporta alta disponibilidad (RAC), particionamiento, seguridad avanzada y procesamiento de transacciones a gran escala. Multiplataforma y multiusuario. Muy utilizado en banca, telecomunicaciones y gobierno. |
| **MySQL**           | Oracle Corp. (código abierto) | DBMS relacional de código abierto, muy popular en aplicaciones web. Ofrece buen rendimiento, facilidad de uso y amplia comunidad. Soporta replicación y es la base de datos detrás de plataformas como WordPress, Facebook y YouTube.                           |
| **SQL Server**      | Microsoft                     | DBMS relacional integrado con el ecosistema Windows y Azure. Incluye herramientas de inteligencia de negocios (BI), análisis de datos y reporting. Ofrece ediciones desde Express (gratuita) hasta Enterprise para grandes organizaciones.                      |

### 2. Entorno Práctico
1. Elaborar una tabla comparativa con recomendaciones, errores comunes y diferencias al instalar DBMS en distintos sistemas operativos (Windows, Linux, Mac, etc.).

|**Aspecto**|**Windows**|**Linux**|**macOS**|
|---|---|---|---|
|**DBMS más comunes**|SQL Server, MySQL, Oracle, PostgreSQL|MySQL, PostgreSQL, MariaDB, Oracle|PostgreSQL, MySQL, SQLite|
|**Método de instalación**|Instaladores gráficos (.exe / .msi). SQL Server usa su propio instalador con asistente paso a paso.|Gestores de paquetes (`apt`, `yum`, `dnf`). Ej: `sudo apt install mysql-server`. También imágenes Docker.|Homebrew (`brew install postgresql`), DMG instaladores, o Docker.|
|**Privilegios requeridos**|Ejecutar como Administrador. SQL Server requiere cuenta de servicio dedicada.|Usuario root o `sudo`. Se crea un usuario de sistema propio (ej: `mysql`, `postgres`).|Permisos de administrador para Homebrew o instaladores .pkg.|
|**Configuración de red/firewall**|Habilitar puertos en Firewall de Windows (ej: 1433 para SQL Server, 3306 para MySQL).|Configurar `iptables`/`ufw` para abrir puertos. Editar `bind-address` en archivos .cnf/.conf.|Firewall menos restrictivo por defecto, pero verificar en Preferencias de Seguridad.|
|**Ruta de datos por defecto**|`C:\Program Files\MySQL\data\` o `C:\Program Files\Microsoft SQL Server\MSSQL\DATA\`|`/var/lib/mysql/` o `/var/lib/postgresql/`|`/usr/local/var/postgres/` (Homebrew) o `/opt/homebrew/var/` (Apple Silicon).|
|**Servicio/daemon**|Se registra como servicio de Windows. Gestión desde `services.msc` o `net start/stop`.|Se gestiona con `systemctl` (systemd). Ej: `sudo systemctl start mysql`.|`brew services start postgresql` o `launchctl` para gestión de daemons.|
|**Errores comunes**|Conflictos de puerto si ya hay otro DBMS instalado. Falta de .NET Framework o Visual C++ Redistributable. Olvidar habilitar TCP/IP en SQL Server.|Olvidar ejecutar `mysql_secure_installation`. Permisos incorrectos en directorios de datos. `bind-address` en 127.0.0.1 impide conexiones remotas.|Problemas de permisos en Apple Silicon (M1/M2/M3). Versiones no compatibles con ARM. Conflictos entre instalación por Homebrew y por .dmg.|
|**Compatibilidad destacada**|SQL Server es nativo y tiene mejor integración. Oracle y MySQL funcionan sin problemas.|Entorno preferido para servidores en producción. Mejor rendimiento y estabilidad para MySQL, PostgreSQL y MariaDB.|Ideal para desarrollo local. SQL Server no tiene versión nativa (se usa Docker). Oracle no soporta macOS oficialmente.|
|**Recomendaciones**|Usar el instalador oficial. Verificar requisitos previos (.NET, RAM, disco). Configurar autenticación mixta en SQL Server.|Siempre correr el script de seguridad post-instalación. Usar `systemctl enable` para inicio automático. Preferir paquetes oficiales del repositorio del proveedor.|Usar Homebrew para simplificar instalación y actualizaciones. Recurrir a Docker para DBMS no soportados nativamente (SQL Server, Oracle).|

---
##### Bibliografía
- Elmasri, R. y Navathe, S. B. (2016). Fundamentals of Database Systems (7.ª ed.). Pearson.
- Silberschatz, A., Korth, H. F. y Sudarshan, S. (2019). Database System Concepts (7.ª ed.). McGraw-Hill.
- Date, C. J. (2004). An Introduction to Database Systems (8.ª ed.).
- Elmasri, R. y Navathe, S. B. (2016). _Fundamentals of Database Systems_ (7.ª ed.). Pearson. Cap. 2.
- Silberschatz, A., Korth, H. F. y Sudarshan, S. (2019). _Database System Concepts_ (7.ª ed.). McGraw-Hill. Cap. 1.
- Oracle Corp. (2025)
- Microsoft (2025)
- PostgreSQL Global Development Group (2025). _PostgreSQL Installation_
- Docker Inc. (2025). _Docker Hub

---
