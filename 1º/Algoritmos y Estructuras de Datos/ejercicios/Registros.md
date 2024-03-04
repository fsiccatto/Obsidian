#### Ejercicio 1
Escribir una declaración de tipo registro que almacene la siguiente información de un libro: título, autor, año, ISBN, páginas y editorial
```
REGISTRO
LIBRO = REGISTRO
	titulo: CADENA
	autor: CADENA
	año: ENTERO
	ISBN: ENTERO
	paginas: ENTERO
	editorial: CADENA
FIN REGISTRO
```
#### Ejercicio 2
Escribir un procedimiento que muestre la información anterior
```
PROCEDIMIENTO mostrarLibro(L: LIBRO)
	INICIO
	ESCRIBIR("Titulo del libro: "), ESCRIBIR(L.titulo)
	ESCRIBIR("Autor del libro: "), ESCRIBIR(L.autor)
	ESCRIBIR("Año de publicacion del libro: "), ESCRIBIR(L.año)
	ESCRIBIR("ISBN del libro: "), ESCRIBIR(L.ISBN)
	ESCRIBIR("Cantidad de paginas del libro: "), ESCRIBIR(L.paginas)
	ESCRIBIR("Editorial del libro: "), ESCRIBIR(L.editorial)
FIN PROCEDIMIENTO
```