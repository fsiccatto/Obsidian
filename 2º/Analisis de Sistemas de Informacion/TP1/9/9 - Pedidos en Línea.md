- 1: Se debe obtener el alta en la página ingresando con sus datos personales: DNI, nombre, dirección, localidad, provincia, celular, mail usuario y contraseña
- 2: Se puede modificar los datos en cualquier momento
- 3: Se puede modificar una o más veces los datos de las tarjetas de crédito
- 4: El sistema valida una vez al día, con los bancos emisores, los datos de las tarjetas registradas en ese día
- 5: Si los datos son correctos, el sistema los confirma como clientes vía mail indicando el número de cliente que le permitirá al cliente efectuar sus compras en línea
- 6: El sistema envía por mail un número de cuenta por cada tarjeta de crédito para los clientes mayoristas.
- 7: Los mayoristas pueden pagar sin tener el dinero en l momento y se va acumulando saldo en su cuenta corriente
- 8: Se requiere que no haya ningún pedido en curso para realizar un nuevo pedido
- 9: El sistema muestra solo productos que tienen stock estimado
- 10: `stock_estimado = stock_real - cant_componentes`
- 11: El sistema debe recharzar pedidos que superen el stock estimado
- 12: Se requiere mostrar los datos del cliente y los detalles de la compra
- 13: Se requiere mostrar lista de productos, descripción, precio unitario, stock estimado y monto total
- 14: Al cerrar el pedido se requiere actualizar el stock, cantidad comprometida del producto, las cantidades pedidas de los productos y se almacena el pedido como pendiente de cobro
- 15: Se requiere pode colocar los pedidos como pendientes de cobro
- 16: Se requiere poder cancelar los pedidos no pagados
- 17: Se requiere guardar historial de pediso
- 18: Se requiere cobrar el pedido por tarjeta de crédito
- 19: Se debe poder cargar/seleccionar otra tarjeta en caso de rechazo
- 20: Se requiere que a minoristas se les cobre en el momento
- 21: Se requiere que a mayoristas se les cobre a principio de mes
- 22: Se debe entregrar el pedido una vez cobrado
### Requisitos
#### Funcionales
- 1: El cliente se registra con datos personales
- 2: El cliente registra su tarjeta
- 3: El cliente realiza un pedido
- 4: El reloj realiza el cobro
- 5: El responsable de pedido cambia el estado a pendiente de entrega
- 6: El cliente modifica sus datos personales
- 7: El cliente modifica sus datos de la tarjeta
- 8: El responsable de distribución cambia de estado de pedido o finalizado
- 9: El cliente mayorista cancela el pedido
- 10: El reloj diariamente consulta datos de nuevos clientes con la AFIP
- 11: El reloj cobra el 1 de cada mes los pedidos mayoristas
### Matriz de Traza
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
### Modelo de Negocio