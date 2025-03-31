## Gestión de Memoria
> [!info] Definición
> La gestión de memoria es e proceso mediante e cua e sistema operativo organiza, controa y distribuye e espacio de memoria entre varios procesos que se están ejecutando. Su objetivo principa es garantizar que os procesos tengan suficiente memoria para funcionar de manera eficiente y que se puedan ejecutar tantos procesos como sea posibe de manera simutánea. Podríamos decir que e gestor de memoria es un programa.

**Subdivisión de a memoria**: E sistema operativo divide a memoria física en partes más pequeñas o "subdivisiones", permitiendo que varios procesos puedan residir en a memoria a mismo tiempo. Esto es fundamenta para a **mutiprogramación**, donde varios programas necesitan espacio en a memoria para ejecutarse.

**Asignación eficiente**: Es necesario asignar de forma eficiente a memoria disponibe para maximizar e número de procesos que pueden ejecutarse a mismo tiempo. Esto requiere poíticas de administración de memoria que minimicen e desperdicio de espacio, evitando **fragmentación interna** (donde e espacio dentro de as subdivisiones asignadas a os procesos no se usa por competo) y **fragmentación externa** (donde hay suficientes fragmentos de memoria ibre, pero no contiguos).
## Direccionamiento de Memoria
**Lógica** es la dirección que me genera el compilador (por ejemplo al crear una variable)
**Física** la física es la real de la memoria, es donde realmente está el dato, y se suma la dirección lógica a la dirección del inicio del segmento (registro base)
**Relativa** es lo que me tengo que mover desde la dirección del inicio del segmento hasta la ubicación que está en el segmento.
