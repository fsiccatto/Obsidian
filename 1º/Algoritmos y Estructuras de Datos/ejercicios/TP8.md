## Actividad 1
1. `LEER(Tomas[4].Muestra[2].Alta`
2. 
```
VARIAR i DESDE 1 HASTA 5
	SI Tomas[5].Muestra[i].Baja > 10 ENTONCES
		ESCRIBIR("Presión BAJA", i ," mayor a 10")
	FIN SI
FIN VARIAR
```
3. `ESCRIBIR("Familiar: ", Tomas[2].Familiar, " Telefono: ", Tomas[2].TelFam)`.
## Actividad 2
```
//declaraciones de Tipos registros Omnibus
TIPO 
OmnibusLarga = REGISTRO 
NroUnidad: ENTERO 
CiudadOrigen: CADENA
CiudadDestino: CADENA
HoraSalida: Tiempo
HoraLlegada: Tiempo
ChoferOmn: Chofer
EstadoAsientos[19]: CARACTER
FIN REGISTRO 

TIPO
Tiempo = REGISTRO 
Hora: ENTERO 
Min: ENTERO
FIN REGISTRO

TIPO 
Chofer = REGISTRO 
NomApe: CADENA 
DNI: ENTERO 
Edad: ENTERO 
FIN REGISTRO
```
![[../imagenes/TP9Ej2.png]]
## Actividad 3
```
//declaraciones de Tipos registros Omnibus
TIPO 
Instituto = REGISTRO 
AlumnoInst: Alumno 
NotasProm: Anio
Amonestaciones: Anio
Faltas: Anio
FIN REGISTRO

TIPO
Alumno = REGISTRO 
NomApe: CADENA 
DNI: ENTERO
Sexo: CARACTER
FIN REGISTRO

TIPO 
Anio = REGISTRO 
Primero: REAL
Segundo: REAL
Tercero: REAL
FIN REGISTRO
```
![[../imagenes/TP9Ej3.jpeg]]