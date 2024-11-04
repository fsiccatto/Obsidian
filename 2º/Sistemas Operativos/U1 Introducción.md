# Sistemas Operativos
> [!info] ¿Qué son los sistemas operativos?
> En términos simples, un sistema operativo es un administrador. Gestiona todos los recursos disponibles en un ordenador. Estos recursos pueden ser el disco duro, una impresora o la pantalla del monitor. Incluso la memoria es un recurso que debe administrarse. 


# Procesos
Cuando se arranca el sistema se inician muchos procesos en forma secreta, lo que a menudo el usuario desconoce. En cualquier instante la CPU está ejecutando sólo un proceso, y en el transcurso de 1 segundo podría trabajar en varios de ellos, dando la apariencia de un paralelismo.
Un proceso no es más que una instancia de un programa en ejecución, incluyendo los valores actuales del contador de programa, los registros y las variables.

## Nivel ISA
El nivel ISA es la interfaz entre el software y el hardware. Define la interfaz entre los compiladores y el hardware; es el lenguaje que ambos tienen que entender.
Una buena ISA:
- Debe definir un conjunto de instrucciones que se pueda implementar con eficiencia en las tecnologías actuales y futuras y permita crear diseños económicos durante varias generaciones.
- Debe ofrecer un objetivo claro para el código compilado, para complacer al hard y al soft.
### Propiedad nivel ISA
- Modo de Kernel ->sirve para ejecutar el sistema operativo y permite la ejecución de todas las instrucciones.
- Modo de usuario -> sirve para ejecutar programas de aplicación y no permite que se ejecuten ciertas instrucciones peligrosas.
### Trampa
Una trampa es iniciada por alguna condición especial causada por el pogrma mismo y detectada por el hardware o microprograma. Por ejemplo un desbordamiento en una suma aritmética.
Las trampas son sincrónicas con el programa. Si el programa se ejecuta mil veces con las mismas entradas, las trampas van a volver a ocurrir en el mismo punto.
### Interrupciones
Son cambios en el flujo de control causados no por el programa en ejecución sino por otra cosa, casi siempre relacionado con E/S.
Las interrupciones son asíncronas con el programa. Las interrupciones podrían variar con las mismas entradas.

