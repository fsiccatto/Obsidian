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

2. Crear y configurar contenedores Docker con imágenes base de Ubuntu (para MariaDB y PostgreSQL) y Oracle Linux (para Oracle Database).
3. Revisión grupal y dinámica de trabajo grupal
- ##### Ajustes y correcciones realizados luego del intercambio grupal
Durante la revisión conjunta del informe se realizaron las siguientes correcciones: se unificó la terminología utilizada en la parte teórica (por ejemplo, estandarizar "DBMS" en lugar de alternar con "SGBD"), se corrigieron errores menores en los comandos de instalación de MariaDB y PostgreSQL dentro de los contenedores Docker, y se reorganizó la tabla comparativa de instalación en distintos sistemas operativos para que fuera más clara y concisa.
- ##### Aportes de cada integrante
|Integrante|Rol|Aportes|
|---|---|---|
|[Integrante 1]|Coordinador general|Organizó las reuniones, distribuyó las tareas, realizó la revisión final del informe completo y unificó el formato de entrega.|
|[Integrante 2]|Investigación teórica|Redactó la clasificación de DBMS según modelo de datos, cantidad de usuarios y distribución geográfica. Recopiló la bibliografía.|
|[Integrante 3]|Análisis comparativo|Elaboró la tabla comparativa de instalación en Windows, Linux y macOS, incluyendo errores comunes y recomendaciones.|
|[Integrante 4]|Entorno práctico (Docker)|Creó y configuró los contenedores Docker para MariaDB y PostgreSQL. Realizó las pruebas de conexión remota desde DBeaver.|
|[Integrante 5]|Entorno práctico (Oracle)|Configuró el contenedor de Oracle Database XE sobre Oracle Linux. Documentó los pasos de conexión desde SQL Developer.|
- ##### Dificultades en la dinámica grupal
La principal dificultad fue la coordinación de horarios, ya que no todos los integrantes tenían disponibilidad en los mismos momentos, lo que retrasó algunas instancias de revisión conjunta. También surgieron problemas técnicos durante la configuración de los contenedores Docker: en particular, la conexión remota a PostgreSQL presentó errores de autenticación que no pudieron resolverse por completo, lo cual requirió más tiempo del planificado. La participación fue relativamente pareja, aunque la carga de trabajo en la parte práctica recayó más sobre \[Integrante 4] e \[Integrante 5], lo cual se compensó con una mayor participación de los demás en la redacción y revisión del informe. Los desacuerdos menores (por ejemplo, qué DBMS comerciales incluir en la comparativa) se resolvieron mediante votación simple dentro del grupo.

---
## Informe grupal
1. Creación de contenedores Docker
```bash
docker run -dit --name mariadb-server -p 3306:3306 ubuntu:22.04
docker run -dit --name postgres-server -p 5432:5432 ubuntu:22.04
docker run -dit --name oracle-server -p 1521:1521 oraclelinux:8
```

2. Instalación y configuración de MariaDB
```bash
docker exec -it mariadb-server bash          # Entrar al contenedor
apt update && apt install -y mariadb-server   # Instalar MariaDB
service mariadb start                         # Iniciar el servicio
mysql_secure_installation                     # Asistente de seguridad (contraseña root, eliminar usuarios anónimos, etc.)
```

Creación de usuario y base de datos:
```sql
mysql -u root -p                              -- Entrar a la consola de MariaDB
CREATE DATABASE laboratorio_bd;               -- Crear la base de datos
CREATE USER 'admin_maria'@'%' IDENTIFIED BY '{password}';  -- Crear usuario accesible desde cualquier IP
GRANT ALL PRIVILEGES ON *.* TO 'admin_maria'@'%';        -- Darle permisos totales
FLUSH PRIVILEGES;                             -- Aplicar los cambios
```

Habilitar conexión remota:
```bash
nano /etc/mysql/mariadb.conf.d/50-server.cnf  # Editar configuración
# Cambiar bind-address = 127.0.0.1 a:
# bind-address = 0.0.0.0
service mariadb restart                        # Reiniciar para aplicar
```

3. Instalción y configuración de PostgresSQL
```bash
docker exec -it postgres-server bash                      # Entrar al contenedor
apt update && apt install -y postgresql postgresql-client  # Instalar PostgreSQL
service postgresql start                                   # Iniciar el servicio
```

Creación de usuario y base de datos
```bash
su - postgres                                 # Cambiar al usuario postgres del sistema
psql                                          # Entrar a la consola
```

```sql
CREATE DATABASE laboratorio_bd;                            -- Crear base de datos
CREATE USER admin_pg WITH PASSWORD '{password}';             -- Crear usuario con contraseña
GRANT ALL PRIVILEGES ON DATABASE laboratorio_bd TO admin_pg;  -- Asignar permisos
ALTER USER admin_pg WITH SUPERUSER;                        -- Darle rol de superusuario
```

Habilitar conexión remota:
```bash
nano /etc/postgresql/14/main/postgresql.conf   # Cambiar listen_addresses = '*'
nano /etc/postgresql/14/main/pg_hba.conf       # Agregar: host all all 0.0.0.0/0 md5
service postgresql restart                     # Reiniciar
```

4. Instalción y configuración de Oracle XE
```bash
docker exec -it oracle-server bash                          # Entrar al contenedor
yum update -y                                               # Actualizar paquetes
yum install -y oracle-database-preinstall-21c               # Instalar dependencias de Oracle
yum install -y oracle-database-xe-21c-1.0-1.ol8.x86_64.rpm # Instalar Oracle XE
/etc/init.d/oracle-xe-21c configure                         # Configurar (pide contraseña para SYS)
```

Variables de entorno y creación de usuario:
```bash
export ORACLE_HOME=/opt/oracle/product/21c/dbhomeXE
export ORACLE_SID=XE
sqlplus sys/password@localhost:1521/XE as sysdba            # Entrar como administrador
```

```sql
ALTER SESSION SET CONTAINER = XEPDB1;                       -- Entrar al pluggable database
CREATE USER admin_ora IDENTIFIED BY {password};               -- Crear usuario
GRANT CONNECT, RESOURCE, DBA TO admin_ora;                  -- Asignar roles
```

5. Conexión desde DBeaver

|Parámetro|MariaDB|PostgreSQL|Oracle|
|---|---|---|---|
|Host|localhost|localhost|localhost|
|Puerto|3306|5432|1521|
|Base de datos|laboratorio_bd|laboratorio_bd|XEPDB1 (Service Name)|
|Usuario|admin_maria|admin_pg|admin_ora|
#### Consideraciones de configuración y acceso
- Es fundamental cambiar el `bind-address` en MariaDB y el `listen_addresses` en PostgreSQL para permitir conexiones desde fuera del contenedor, ya que por defecto ambos solo escuchan en `127.0.0.1` (localhost interno del contenedor).
- En PostgreSQL además hay que modificar `pg_hba.conf` para autorizar conexiones por contraseña desde cualquier IP.
- Oracle XE ya viene con el listener habilitado en el puerto 1521, por lo que no requiere configuración adicional para conexión remota.
- Al reiniciar la PC, los contenedores se detienen. Hay que levantarlos con `docker start` y luego iniciar manualmente los servicios dentro de cada contenedor.

### Problemas encontrados y cómo se resolvieron
**MariaDB – Access denied for user 'admin_maria'@'%':** El usuario se había creado con permisos solo sobre la base `practico_bd`, pero en DBeaver se intentaba conectar a `laboratorio_bd`. Se resolvió otorgando permisos sobre todas las bases con `GRANT ALL PRIVILEGES ON *.* TO 'admin_maria'@'%'` y creando la base con el nombre correcto.

**PostgreSQL – FATAL: la autenticación password falló para el usuario 'admin_pg':** Al intentar conectar desde DBeaver, PostgreSQL rechazaba la contraseña del usuario. Se intentó resetear la contraseña con `ALTER USER admin_pg WITH PASSWORD 'password'` y también se cambió temporalmente el método de autenticación en `pg_hba.conf` de `md5` a `trust` para descartar problemas de encriptación. A pesar de estas medidas, el error persistió y no se logró establecer la conexión remota desde DBeaver. Se sospecha que el problema puede estar relacionado con la versión del driver JDBC de PostgreSQL en DBeaver o con la configuración interna de autenticación del contenedor. Queda pendiente como punto a resolver en una futura iteración del trabajo.

**Docker Desktop – Virtualización no detectada:** Al iniciar Docker Desktop se mostró el error "virtualization support wasn't detected". Se resolvió ingresando a la BIOS del equipo y habilitando la opción Intel VT-x (o AMD SVM según el procesador), tras lo cual Docker inició correctamente.

Docker:
![[docker.png]]

Conexiones:
![[dbeaver.png]]

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
