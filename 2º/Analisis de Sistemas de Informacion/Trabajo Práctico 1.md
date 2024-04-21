# Captura de Requisitos con Casos de Uso
> [!faq]- Práctica a realizar
>  1. Lista de Características
>  2. Matriz de Traza
>  3. Lista de Requisitos Funcionales
>  4. Lista de Requisitos No Funcionales 
>  5. Modelo del Negocio 
>  6. Modelo del Dominio
>  7. Diagrama de casos de uso
>  8. Especificación de casos de uso
>  9. Diagrama de clases
>  10. Máquina de estados
>  11. Diagrama de colaboración
## 9 - Gestión de pedidos en línea
#### Características
C1: Se debe obtener el alta en la página ingresando con sus datos personales: DNI, nombre, dirección, localidad, provincia, celular, mail usuario y contraseña
C2: Se puede modificar los datos en cualquier momento
C3: Se puede modificar una o más veces los datos de las tarjetas de crédito
C4: El sistema valida una vez al día, con los bancos emisores, los datos de las tarjetas registradas en ese día
C5: Si los datos son correctos, el sistema los confirma como clientes vía mail indicando el número de cliente que le permitirá al cliente efectuar sus compras en línea
C6: El sistema envía por mail un número de cuenta por cada tarjeta de crédito para los clientes mayoristas.
C7: Los mayoristas pueden pagar sin tener el dinero en l momento y se va acumulando saldo en su cuenta corriente
C8: Se requiere que no haya ningún pedido en curso para realizar un nuevo pedido
C9: El sistema muestra solo productos que tienen stock estimado
C10: `stock_estimado = stock_real - cant_componentes`
C11: El sistema debe recharzar pedidos que superen el stock estimado
C12: Se requiere mostrar los datos del cliente y los detalles de la compra
C13: Se requiere mostrar lista de productos, descripción, precio unitario, stock estimado y monto total
C14: Al cerrar el pedido se requiere actualizar el stock, cantidad comprometida del producto, las cantidades pedidas de los productos y se almacena el pedido como pendiente de cobro
C15: Se requiere pode colocar los pedidos como pendientes de cobro
C16: Se requiere poder cancelar los pedidos no pagados
C17: Se requiere guardar historial de pediso
C18: Se requiere cobrar el pedido por tarjeta de crédito
C19: Se debe poder cargar/seleccionar otra tarjeta en caso de rechazo
C20: Se requiere que a minoristas se les cobre en el momento
C21: Se requiere que a mayoristas se les cobre a principio de mes
C22: Se debe entregrar el pedido una vez cobrado
#### Requisitos
> [!summary] Funcionales
> R1: El cliente se registra con datos personales
> R2: El cliente registra su tarjeta
> R3: El cliente realiza un pedido
> R4: El reloj realiza el cobro
> R5: El responsable de pedido cambia el estado a pendiente de entrega
> R6: El cliente modifica sus datos personales
> R7: El cliente modifica sus datos de la tarjeta
> R8: El responsable de distribución cambia de estado de pedido o finalizado
> R9: El cliente mayorista cancela el pedido
> R10: El reloj diariamente consulta datos de nuevos clientes con la AFIP
> R11: El reloj cobra el 1 de cada mes los pedidos mayoristas
#### Matriz de Traza

|     | R1  | R2  | R3  | R4  | R5  |
| :-- | :-- | :-: | :-: | :-: | :-: |
| C1  | X   |     |     |     |     |
| C2  |     |  X  |     |     |     |
| C3  |     |  X  |     |     |     |
| C4  | X   |     |     |     |     |
| C5  | X   |     |     |     |     |
| C6  |     |     |  X  |     |     |
| C7  |     |     |  X  |     |     |
| C8  |     |     |  X  |     |     |
| C9  |     |     |  X  |     |     |
| C10 |     |     |  X  |     |     |
| C11 |     |     |  X  |     |     |
| C12 |     |     |  X  |     |     |
| C13 |     |     |  X  |     |     |
| C14 |     |     |  X  |     |     |
| C15 |     |     |  X  |     |     |
| C16 |     |     |  X  |     |     |
| C17 |     |     |  X  |     |     |
| C18 |     |     |     |  X  |     |
| C19 |     |     |     |  X  |     |
| C20 |     |     |     |  X  |     |
| C21 |     |     |     |  X  |     |
| C22 |     |     |     |     |  X  |

![[7-Modelo de Negocio]]
## 10 - Proyecto Gym Fit+
#### Características
C1: Un profesor puede abrir una clase estableciendo fecha y hora
C2: Un cliente puede comprar clases a $200 cada una
C3: La cantidad mínima de clases que puede comprar un socio es 3
C4: La cantidad máxima de clases que puede comprar un socio es 20
C4: Un socio puede reservar una o más clases para asistir
C5: Las clases tienen duración de 1 hora
C6: Un socio no puede inscribirse a una clase llena o cerrada
C7: La cantidad máxima de personas por clase es de 50
C8: El sistema debe llevar un control de la cantidad de clases consumidas por el socio
C9: El socio no podrá ingresar si ya consumió el 100% de sus clases
C10: Se le permitirá adquirir, al socio, más clases si le quedan 3 o menos disponibles
C11: `Cuota_Total = Precio_Clase * Cant_Clases`
C12: Si un cliente se anota por primera vez, el sistema le pedirá los datos personales
C13: Si el socio no asiste a una clase que tenía reservada, esta se pierde
C14: El gerente quiere un sistema de ingreso
C15: El sistema de ingreso debe ser biométrico o con credencial
C16: El sistema debe mostrar solamente las clases disponibles y que no estén ocupadas totalmente
#### Requisitos
> [!summary] Funcionales
> R1: El cliente compra un número de clases
> R2: El cliente se anota a una clase que esté disponible y abierta
> R3: El sistema lleva el control de cada cliente
> R4: 


> [!tip] No Funcionales
