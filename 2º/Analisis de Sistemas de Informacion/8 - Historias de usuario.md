# Historias de Usuario
Las historias de usuario son una herramienta clave en las metodologías ágiles, utilizadas para describir brevemente los requisitos del software desde la perspectiva del usuario final. Su propósito es capturar de manera simple y narrativa lo que el usuario necesita, fomentando la comunicación entre los equipos de desarrollo y los clientes.

## Estructura de una Historia de Usuario
Una historia de usuario sigue un formato claro y conciso:

**Formato**: "Como [rol de usuario], quiero [objetivo] para [beneficio]".

### Elementos esenciales:
1. **ID**: Identificador único para la historia de usuario.
2. **Descripción**: Breve narrativa que explica quién es el usuario, qué necesita y cuál es el beneficio.
3. **Estimación**: Medida del esfuerzo necesario, ya sea en puntos de historia o tiempo.
4. **Prioridad**: Nivel de importancia o urgencia para ser implementada.

Además de estos elementos, se puede añadir información adicional como el criterio de validación (pruebas que confirman que la historia fue implementada correctamente), dependencias con otras historias, y quién es el responsable dentro del equipo.

## Ventajas de una Historia de Usuario
- **Simplicidad**: Son fáciles de entender y gestionar, con una narrativa clara.
- **Implementación rápida**: Se pueden desarrollar en poco tiempo (días o semanas).
- **Adaptabilidad**: Ideales para proyectos con requisitos volátiles o cambiantes.
- **Colaboración cercana con el cliente**: El cliente participa activamente al expresar sus necesidades en su propio lenguaje.
- **Estimación más fácil**: Ayudan a estimar el esfuerzo de desarrollo de forma precisa.

## Jerarquía en el Backlog
Las historias de usuario se organizan dentro del backlog, junto con:

- **Épicas**: Historias de gran tamaño que abarcan más funciones o requisitos generales.
- **Tareas**: Acciones más pequeñas y específicas derivadas de las historias de usuario.

Las historias de usuario son más detalladas que las épicas y, al igual que las tareas, se ordenan por prioridad en el backlog. El nivel de detalle aumenta cuanto más prioritaria es la historia, mientras que las épicas suelen estar en la parte baja del backlog, con menos urgencia.

# Criterios de Aceptación
Los criterios de aceptación definen las pruebas que debe pasar la historia para considerarse finalizada. Estos pueden escribirse en lenguaje natural o mediante técnicas como **BDD** (Behavior-Driven Development). Deben ser específicos y medibles para asegurar que los requisitos sean claros.

## Calidad en las Historias de Usuario
Existen dos metodologías para garantizar la calidad de una historia de usuario:

- **SMART**: Los criterios de aceptación deben ser:
  - Específicos, Medibles, Alcanzables, Relevantes y Temporales.

- **INVEST**: La historia debe cumplir con estas características:
  - **Independiente**: Se puede implementar sin depender de otras historias.
  - **Negociable**: Sus detalles son ajustables durante la conversación con el cliente.
  - **Valiosa**: Debe ofrecer valor real al cliente o usuario.
  - **Estimable**: Debe ser posible estimar el esfuerzo necesario para completarla.
  - **Pequeña**: Debe ser lo suficientemente breve como para desarrollarse en poco tiempo.
  - **Comprobable**: Debe ser posible probar su implementación con criterios de validación claros.

# Prioridad y Valor en las Historias de Usuario
La priorización de las historias de usuario es clave para enfocar el trabajo en aquellas que aportan mayor valor al sistema. Es fundamental distinguir entre:

- **Valor para el cliente**: Historias que cubren necesidades específicas del usuario.
- **Valor para el equipo de desarrollo**: Historias que son esenciales para el funcionamiento del sistema, más allá de la demanda directa del cliente.

La priorización no se basa solo en la clasificación clásica (alta, media, baja), sino que es recomendable utilizar una escala cualitativa con preguntas clave como:

- ¿Es necesario?
- ¿Es recomendable?
- ¿Podría implementarse?
- ¿Es algo que queremos ahora o en el futuro?

### Clasificación de prioridades:
1. **Necesario**: Funcionalidad crítica para el éxito del producto.
2. **Recomendable**: Alta prioridad para el funcionamiento del sistema.
3. **Podría implementarse**: Funcionalidad deseable, pero no urgente.
4. **No lo queremos ahora**: Funcionalidad de baja prioridad o que puede ser evaluada en el futuro.

# División de Historias de Usuario
Para gestionar de forma efectiva las historias de usuario, especialmente las más grandes (épicas), es útil dividirlas en historias más pequeñas. Esto facilita su estimación, priorización y entrega.

### Tipos de División:
- **División Horizontal**: Separar las historias por tecnologías o tareas (diseño, base de datos, frontend, pruebas). Aunque es una opción, no genera valor de negocio de forma individual.
- **División Vertical**: Más recomendada, consiste en dividir una historia en componentes que aporten valor al negocio. Un ejemplo sería dividir la funcionalidad de búsqueda de productos en varios parámetros: por número de producto, por rango de precios, por color, etc.

# Comparación con Casos de Uso
Las historias de usuario y los casos de uso tienen varias diferencias clave:

- **Formato**: Las historias de usuario son narrativas y breves, mientras que los casos de uso son más detallados y gráficos.
- **Participación**: En los casos de uso participan stakeholders y analistas. En las historias de usuario, participan stakeholders y todo el equipo de desarrollo.
- **Duración**: Los casos de uso describen funcionalidades completas, mientras que las historias de usuario están limitadas a ciclos cortos (sprints).
- **Criterios de aceptación**: Las historias de usuario siempre incluyen criterios de aceptación, algo que no es común en los casos de uso.

# Historias de Usuario vs. Requisitos Funcionales
Al igual que los requisitos funcionales, las historias de usuario describen **el qué** se quiere lograr, pero no **el cómo**. Sin embargo, las historias de usuario no son tan detalladas como una especificación funcional formal. Su objetivo es captar la necesidad de manera simple y comprensible.

# Técnica de User Story Mapping
La técnica de **User Story Mapping** permite construir la pila de producto (**product backlog**) mediante la creación de un mapa de historias de usuario que representa las distintas funcionalidades y alternativas.

### Ejemplo:
- **Actividad principal**: Venta online.
- **Secuencia de actividades**: Buscar producto, agregar al carrito, pagar.
- **Alternativas**:
  - Buscar por nombre, categoría o precio.
  - Pagar con tarjeta de débito, crédito, o MercadoPago.

Este proceso ayuda a organizar y priorizar las historias de usuario para crear un backlog claro y alineado con los objetivos del producto.
