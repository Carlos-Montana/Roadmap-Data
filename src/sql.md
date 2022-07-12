## SQL (Structured Query Lenguage)

- tipos de datos:
	- char
	- varchar
	- text
	- tinyInt
	- Int
	- BigInt
	- Double
	- Date
	- DateTime

- Tiposde consultas:
	- Estructura de la base de dato:
	  - CREATE DATABASE -> cread db
	  - DROP DATABASE -> eliminar db
	  - CREATE TABLE -> crear tabla
	  - ALTER TABLE -> modificar tabla
	  - DROP TABLE -> eliminar tablas
	- Consultando y Modificando los Datos:
	  - SELECT -> Buscar
	  - INSERT -> Agregar
	  - UPDATE -> Modificar
	  - DELETE -> Eliminar

*Estos son comando basicos, existen varios mas, pero aprender estos que son super importantes.*<br>

ejemplo:<br>
`CREATE TABLE usuarios(
id int(11) NOT NULL AUTO_INCREMENT,
nombre varchar(80) NOT NULL,
apellido varchar(80) NOT NULL,
fecha_nacimiento DATETIME NULL,
PRIMARY KEY (id)
);`<br>
*siempre se agrega ; al final de cada comando de sql*

Para borrar tabla:<br>
DROP TABLE IF EXIST(opcional)<br>

agragar/modificar columnas:<br>
ALTER TABLE usuarios ADD/MODIFY COLUMN telefono varchar(45) NULL;<br>

eliminar columnas:<br>
ALTER TABLE usuarios DROP telefono;<br>

modificar columnas:<br>
ALTER TABLE usuarios ALTER COLUMN telefono varchar(35) NULL;<br>

sqlfiddle.com(web para programar sql en linea)<br>
workbench (herramienta profesional)<br>

Agregar eliminar datos:<br>

`INSERT INTO usuarios(
nombre,apellio,fecha_nacimiento,telefono)
VALUES('carlos','montaña','1988-06-25 18:00:00','123456897');` /*usar comillas simples para todos los datos*/<br>

eliminar fila:<br>
DELETE FROM usuarios WHERE id = '1';<br>

modificar un dato:<br>
UPDATE usuarios
SET nombre='javier',
apellido='Aguirre'
WHERE id='1';

Consultar datos:<br>

buscar todo los usuarios:<br>
SELECT * FROM usuarios;<br>

busca el usuario con ID 1:<br>
SELECT * FROM usuarios WHERE id='1';<br>

buscar el nombre y apellido del usuario con id 1:<br>
SELECT nombre, apellido FROM usuarios WHERE id='1'<br>

Realizamos una consulta mas compleja:<br>

SELECT COUNT (*) as 'cantidad' FROM usuarios WHERE apellido ='mantaña' AND/OR nombre = 'carlos'; <br>
esta sentencia utiliza COUNT para contar el total de filas, y en este caso tambie se pone as para que cuando muestre el resultado la columna se llame cantidad le asignamos ese nombre.Por otro lado despues del WHERE podemos poner mas de una sentencia que deba cumplir con el AND U OR.<br>

Para buscar un texto dentro de nuestra base de datos usamos LIKE:<br>
SELECT * FROM ususarios WHRER nombre LIKE 'lucas' // tambien le podemos poner variantes como 'luc%', busca todo lo que empieze con luc y tenga cualquiero cosa despues, y tambien '%uc%' busca texto que contenga uc y adelante y atras cualquier cosa.<br>

Claves Foraneas(para entrelazar las tablas)
 -creamos la tabla y para terminamos le poneslo el FOREIGN KEY (nombre_del_element) REFERENCE usuarios(nombre_del_elemente_referido)
  `CREATE TABLE usuarios(
id int(11) NOT NULL AUTO_INCREMENT,
nombre varchar(80) NOT NULL,
apellido varchar(80) NOT NULL,
fecha_nacimiento DATETIME NULL,
PRIMARY KEY (id)
);`<br>
`CREATE TABLE publicaciones(
id int(11) NOT NULL AUTO_INCREMENT,
autor_id NOT NULL,
titulo varchar(160) NOT NULL,
texto text NOT NULL,
PRIMARY KEY (id),
FOREIGN KEY (autor_id) REFERENCES usuarios(id)
);`<br>

consultas complejas:<br>
`SELECT p.asterisco,
CONCAT(u.nombre,'',u.apellido) as 'autor'
FROM publicaciones p, usuarios u
WHERE p.autor_id = u.id;
	esta consulta asigna letras a la tablas en la parte del from, 
	luego el select selecciona todo la tabla p(publicaciones), luego
	concat une nombre y apellido en una sola columna para mostrar de la 
	tabla de usuarios, y por ultimo en el where ponemos la condicion
	de el autor id de p sea igual el de u. De esta manera tenemos dos
	tablas que se referencian.(cabe aclarar que este tipo de consultas con muchos
	datos tardaria mucho, y funciona tanto si estas relacionadas o no las tablas, por
	lo cual no es lo mas optimo para tablas relacionadas con foreign key, asique a 
	continuacion se vera la manera optima con join)`
	`
<br>

SELECT p.*,
CONCAT(u.nombre,'',u.apellido) as 'autor'
FROM publicaciones p INNER JOIN usuarios u
ON p.autor_id = u.id; <br>

- Funciones de agregación de sql:
	- COUNT(asterisco)//cuenta la cantidad de filas
	- MAX(puntaje)//devuelve el maximo puntaje
	- MIN(puntaje)//devuelve el minimo puntaje
	- AVG(puntaje)//devuelve el puntaje promedio
	- SUM(precio)//devuelve una sumatoria de precios<br>
	- ejemplo generico:
		SELECT MAX(nombre_variable) from nombre_tabla
<br>

*Algunos ejemplos de otras funciones:*<br>
select asterisco from curso.usuarios where nombre like 'L%'<br>
UNION //sirve para unir dos o mas consultas diferentes.<br>
select asterisco from curso.usuarios where nombre like 'P%'<br>

select * from curso.usuarios group by apellido // <br>group by sirve para que no se repitan filas al momento de mostrar resultados<br>
[Volver](../README.md)
