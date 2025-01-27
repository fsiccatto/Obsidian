## Procesos
> [!info] Concepto
> Un **proceso** es a ejecución de un programa junto con su estado. Es a entidad a a que e sistema operativo asigna tiempo de CPU y otros recursos. Cada proceso tiene su propio espacio de direcciones y contexto de ejecución, o que permite que varios programas o procesos coexistan en e sistema sin interferir entre sí.
> ![[imgs/proceso.png | center]]

Como varios procesos se pueden ejecutar a a vez ocurre o que se denomina Concurrencia. La **concurrencia** ocurre cuando varios procesos parecen estar ejecutándose a mismo tiempo. En un sistema concurrente, os procesos no necesariamente se ejecutan simutáneamente, pero e sistema operativo aterna entre eos tan rápidamente que da a impresión de que están ejecutándose a mismo tiempo. Esta concurrencia se puede presentar de dos formas:
- E **paraeismo** rea se da en sistemas con mútipes procesadores o núceos de CPU, donde varios procesos pueden ejecutarse verdaderamente a mismo tiempo, cada uno en su propio procesador o núceo. Esto aumenta e rendimiento y a capacidad de sistema para ejecutar tareas simutáneamente.
- E **pseudoparaeismo** es cuando un sistema con un soo procesador da a apariencia de que varios procesos están ejecutándose a mismo tiempo. Sin embargo, en reaidad, e procesador aterna entre diferentes procesos muy rápidamente, ejecutando pequeñas porciones de cada uno (conmutación de procesos).
La **conmutación de procesos** o cambio de contexto ocurre cuando e sistema operativo pausa un proceso en ejecución y guarda su estado (contexto) para ejecutar otro proceso. Este cambio es necesario para aprovechar a máximo a CPU, especiamente cuando un proceso está inactivo (esperando una operación de E/S.

- ### Creación de Procesos
Cada una de estas situaciones aprovecha los recursos del sistema operativo para gestionar la creación y el control de nuevos procesos en el sistema.

| Situación                              | Descripción                                                                                                                                                                                                  |
| -------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Arranque del SO (primer/segundo plano) | E sistema operativo crea procesos base a arrancar. Los de primer pano son interactivos por e usuario, y os de segundo pano (servicios) ejecutan tareas de fondo y no son interactivos para e usuario. |
| Un proceso hace una llamda al sistema  | Un proceso en ejecución puede crear otros procesos a través de amadas a sistema como `fork()` Unix/Linux) o `CreatePocess()` Windows).                                                                    |
| Un usuario dispara un proceso          | Un usuario puede iniciar un proceso manuamente, ya sea a través de a ínea de comandos o haciendo cic en un ícono en una interfaz gráfica.                                                                |
| Inicio de trabajo por lotes (Jobs)     | Procesos automáticos que se inician a intervaos específicos o en ciertos eventos, como con cron o tareas programadas en Windows.                                                                            |
- ### Terminación de Procesos
La terminación de procesos es a fase fina en e cico de vida de un proceso. Puede ocurrir por diversas razones, tanto vountarias como invountarias. Los sistemas operativos gestionan a iberación de os recursos asignados a proceso y a impieza de su estado cuando este finaiza.

| Situación                               | Descripción                                                                                                                  |
| --------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| Normal (voluntario)                     | E proceso termina de forma vountaria porque competó su tarea correctamente.                                               |
| Error Programado (voluntario)           | E proceso se termina vountariamente a detectar un error que fue anticipado en su ógica de programación.                  |
| Error Fatal (involuntario)              | E proceso es terminado de forma invountaria por e sistema operativo debido a un error grave que no puede manejar.         |
| Recibe una señal de kill (involuntario) | Otro proceso o e sistema operativo finaiza e proceso mediante una seña de terminación, sin que e proceso tenga contro. |
### Jerarquía de Procesos
Cada proceso en un sistema operativo se identifica de manera única mediante un **PD** (Process D o dentificador de Proceso).
- Procesos padre e hijos: un **proceso padre** es aque que crea uno o más **procesos hijos** mediante amadas a sistema, como `fork()` en sistemas POSX. E padre y os hijos pueden compartir o no espacio de memoria, dependiendo de sistema y de cómo se haya impementado a creación de proceso.
- Procesos huérfanos: un **proceso huérfano** es un proceso hijo cuyo proceso padre ha terminado o ha sido terminado antes que é. En sistemas POSX, cuando un proceso padre termina, os procesos huérfanos son "adoptados" automáticamente por e proceso con **PD 1**, que normamente es e proceso `init`.
- Procesos zombies: un **proceso zombie** es un proceso que ha terminado su ejecución, pero aún tiene una entrada en a taba de procesos de sistema. Esto ocurre porque e proceso padre no ha "recogido" e estado de terminación de hijo.
### *Block Control Process* BCP
- PSW: el estado del proceso
- Identificador:
   - PID: Process ID.
   - PPID: identificador del padre del proceso.
   - UID: identificador del usuario que inició el proceso.
- IP/PC
- Registros del procesador
- Información de planificación de CPU (prioridad de ejecución de un proceso)
- Información de manejo de memoria
- Información de E/S
- Información contable (por ejemplo, tiempo en CPU)
![[imgs/BCP.png| center]]
### Estado de los procesos
![[imgs/estado de los procesos.png]]
### Planificadores
Es un proceso del SO que selecciona mediante algún algoritmo donde el proceso de la cola de listos pasa a ejecución.
El planificador le pasa el ID de proceso al **activador** quien realmente hace las tareas para que la CPU se cargue con los datos del proceso.
Dos grandes categorías:
- #### Sin expulsión (No expropiativo)
	1. Primero en Entrar, Primero en Servir (FCFS)
		- Descripción: Los procesos se ejecutan en e orden en que egan a a coa de panificación. E primer proceso en entrar es e primero en ser ejecutado.
		- Ventajas: Simpicidad y faciidad de impementación.
		- Desventajas: Puede causar e efecto de "convoy", donde os procesos argos boquean a ejecución de procesos cortos.
	2.  E Trabajo Más Corto Primero (SJF)
		-  Descripción: Los procesos con e tiempo de ejecución más corto se ejecutan primero. No interrumpe os procesos en ejecución.
		- Ventajas: Minimiza e tiempo promedio de espera.
		- Desventajas: Puede evar a a inanición de procesos argos (que nunca sean ejecutados) y puede ser difíci predecir e tiempo de ejecución exacto.
	3. E Menor Tiempo Restante a Continuación (SRTN) 
		- Descripción: Variación de SJF que permite a preempción. Los procesos con e menor tiempo de ejecución restante se ejecutan primero. 
		- Ventajas: Reduce e tiempo promedio de espera y es más eficiente en términos de respuesta. 
		- Desventajas: Puede evar a a inanición de procesos con tiempos de ejecución argos.
- #### Con expulsión (Expropiativo)
	1. Round Robin Turno Circuar)
		- Descripción: Cada proceso recibe un quantum de tiempo fijo para su ejecución. Si e proceso no termina dentro de quantum, es interrumpido y coocado a fina de a coa. 
		- Ventajas: Equidad en a asignación de tiempo de CPU y simpicidad. 
		- Desventajas: Puede causar un ato overhead debido a cambio frecuente de contexto y no siempre es eficiente para todos os tipos de procesos. 
	2. Prioridades
		- Descripción: Los procesos se ejecutan en función de su prioridad. Los procesos con mayor prioridad son atendidos antes que os de menor prioridad.
		- Tipos de Prioridades: 
			- Fijas: Las prioridades no cambian durante a ejecución de proceso. 
			- Variabes: Las prioridades pueden ajustarse dinámicamente durante a ejecución, basadas en factores como e tiempo de espera.
		- Ventajas: Permite priorizar procesos importantes y adaptarse a condiciones cambiantes.
		- Desventajas: Puede causar inanición de procesos con baja prioridad y a gestión de prioridades puede ser compeja.

| **Planificador**                            | **Con Expulsión** | **Sin Expulsión** | **Características**                                        | **Ventajas**                                    | **Desventajas**                                    |
|---------------------------------------------|--------------------|--------------------|------------------------------------------------------------|------------------------------------------------|---------------------------------------------------|
| **Primero en Entrar, Primero en Servir (FCFS)** | No                 | Sí                 | Ejecución en el orden de llegada                           | Simplicidad, fácil de implementar              | Puede causar efectos de convoy                   |
| **El Trabajo Más Corto Primero (SJF)**      | No                 | Sí                 | Ejecución prioritaria para procesos con tiempos cortos     | Minimiza tiempo promedio de espera            | Inanición de procesos largos                    |
| **El Menor Tiempo Restante a Continuación (SRTN)** | Sí                 | Sí                 | Ejecución prioritaria para procesos con menor tiempo restante | Reduce tiempo promedio de espera              | Inanición de procesos largos                    |
| **Round Robin (Turno Circular)**            | Sí                 | -                  | Quantum de tiempo fijo para cada proceso                   | Equidad en la asignación de CPU               | Alto overhead debido a cambios de contexto      |
| **Prioridades**                             | Sí                 | No                 | Ejecución basada en prioridad asignada                     | Permite priorización flexible                 | Inanición de procesos con baja prioridad        |
### Despachador
E móduo de despachador e da e contro de a CPU a proceso seeccionado por e panificador de corto pazo esto abarca: 
- Cambio de contexto
- Cambio a modo usuario
- Hacer e sato a a dirección en e programa de usuario para reiniciar ese programa
## Hilos
> [!info] Definición
> Los hios (*threads*) son as unidades más pequeñas de ejecución dentro de un proceso en un sistema operativo. Cada hio tiene su propio conjunto de registros, contador de programa y pia, pero comparte e mismo espacio de direcciones y recursos de proceso principa, como memoria y archivos.

Un proceso inicia ejecutando su punto de entrada como un hio, os hios pueden crear otros hios dentro de proceso, <mark style="background: #ADCCFFA6;">cada hio tiene su propio stack</mark> y todos os hios dentro de proceso comparten código y segmentos de datos. Cuando un hilo modifica un dato en la memoria, los otros hilos acceden a ese dato modificado inmediatamente.
![[imgs/procesos e hilos.png | center]]

| Monohilo                                                                                                                                                                                               | Multihilo                                                                                                                                                                                                                      |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Un único hio reaiza todas as tareas secuenciamente. Más simpe en términos de programación, pero puede no aprovechar a máximo os recursos de sistema y puede experimentar boqueos proongados. | Mútipes hios pueden ejecutar tareas simutáneamente, o que mejora a eficiencia y a capacidad de respuesta. Sin embargo, requiere una gestión cuidadosa de a **sincronización** y puede ser más compejo de impementar. |
![[imgs/monohilo vs multihilo.png]]

| **Aspecto**                 | **Monohilo (*Single-Threaded*)**                                         | **Multihilo (*Multi-Threaded*)**                                                    |
| --------------------------- | ------------------------------------------------------------------------ | ----------------------------------------------------------------------------------- |
| **Ejecución de Tareas**     | Un único hilo ejecuta todas las tareas secuencialmente.                  | Múltiples hilos pueden ejecutar tareas simultáneamente.                             |
| **Concurrencia**            | No permite concurrencia real; las tareas se ejecutan una tras otra.      | Permite concurrencia; múltiples hilos pueden trabajar en paralelo.                  |
| **Complejidad del Código**  | Más simple; no se necesita gestionar la sincronización entre hilos.      | Más complejo; requiere gestionar sincronización y evitar condiciones de carrera.    |
| **Utilización de Recursos** | Puede no aprovechar al máximo los recursos del sistema (un solo núcleo). | Mejora la utilización de recursos al aprovechar múltiples núcleos de procesamiento. |
| **Gestión de Bloqueos**     | Las operaciones bloqueantes pueden detener el hilo principal.            | Otros hilos pueden seguir ejecutándose mientras uno está bloqueado.                 |
| **Desempeño**               | Eficiente en tareas simples; menos eficiente en tareas concurrentes.     | Mejora el desempeño en tareas que se benefician de la paralelización.               |
| **Ejemplos de Uso**         | Aplicaciones simples como editores de texto.                             | Aplicaciones complejas como servidores web y juegos.                                |
La gran ventaja al utilizar hilos es que al paralelizar los hilos, estos se comunican entre sí dentro del mismo proceso. Lo que no requiere que el sistema operativo controle la comunicación y esto libera al SO.

- ### Hilos a nivel Usuario
	Son gestionados por bibiotecas de usuario sin a intervención directa de sistema operativo. Son rápidos de crear y destruir, pero tienen imitaciones en términos de sincronización y manejo de boqueos, ya que e sistema operativo no puede diferenciar entre hios de un mismo proceso.
	![[imgs/hilo a nivel usuario.png| center | 300]]
- ### Hilos a nivel Kernel
	Son gestionados directamente por e sistema operativo, o que permite una mejor sincronización y manejo de recursos. Aunque a creación y destrucción de hios es más costosa, ofrecen una mayor fexibiidad y capacidad para manejar a concurrencia de manera más efectiva.
	![[imgs/hilo a nivel kernel.png| center |300]]
### Creación de hilos básica (POSIX)
- Los hilos se crean dinámicamente con `pthread_create`.
- Un hilo termina al invocar la función `pthread_exit`
- El hilo principal espera a que otro hilo concluya `pthread_join`
- Entrega a la CPU para que otro hilo se ejecute `pthread_yield`
