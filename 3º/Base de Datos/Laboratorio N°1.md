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

##### Bibliografía
• Elmasri, R. y Navathe, S. B. (2016). Fundamentals of Database Systems (7.ª ed.). Pearson.
• Silberschatz, A., Korth, H. F. y Sudarshan, S. (2019). Database System Concepts (7.ª ed.). McGraw-Hill.
• Date, C. J. (2004). An Introduction to Database Systems (8.ª ed.).
• Oracle Corp. (2025). Oracle Database Documentation.