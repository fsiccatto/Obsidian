### Caracterísiticas
1. se necesita registrar la interanción de un paciente
2. se necesita registrar pacientes con o sin obra social
3. se necesita acceder a un nomenclador de prestaciones preestablecido
4. se necesita que la administración cobre a la Obra Social el último día hábil del mes
5. se necesita ingresar los datos de la Obra Social y el plan del paciente y se valida si están dentro del convenio
6. si está dentro del convenio, se necesita informar al paciente el importe de coseguros (si corresponde)
7. si no está dentro del convenio, se necesita informar los importe asociados al nomenclador en caso de no tener obra social
8. se necesita calcular el importe en función de la prestación y el porcentaje de coseguro asociado al plan de la obra social
9. se necesita que el sistema muestre los datos del paciente, y se pueden modificar estos datos
10. se necesita ingresar los datos del paciente, en caso de que no se encuentre en el sistema
11. se necesita que el sistema establezca el tipo de habitación que le corresponde y muestre las camas disponibles
12. se necesita que en el sistema se ingresen los datos relevantes de los informes de laboratorio de rutina, examen médico y cardiológico
13. se necesita que el sistema imprima el comprobante de pago en el que se detallan los datos del paciente, importe a abonar y la cama
14. se necesita que el sistema almacene el ingreso a internación, historia clínica, asignación de camas y médicos.
### Requisitos
> [!tldr] Funcionales
> 1. El paciente solicita internación
> 2. El paciente informa resultados de estudios en su Historia Clínica
> 3. El paciente finaliza la internación al ser dado de alta
> 4. El encargado de obra social paga servicios del paciente
> 5. El administrador de clínica genera resumen para que paguen las obras sociales
> 6. El administrador del sistema administra tipos de presentación
> 7. El administrador del sistema gestiona prestaciones (nomenclador)
> 8. El administrador del sistema gestiona obras sociales
> 9. El administrador del sistema administra planes de cada obra social
> 10. El administrador del sistema administra coseguros a pagar de planes de obras sociales por prestación
> 11. El administrador del sistema administra los tipos de habitación por tipo de prestación
> 12. El administrador del sistema gestiona camas por tipo de habitación
### Modelo Casos de Uso
![[4-Modelo de Casos de Uso]]
### Modelo de Dominio
 ![[4-Modelo de Dominio]]