
### 1. Completa el siguiente test.

##### a. Una dirección postal se debe almacenar en un campo de tipo VARCHAR:
* ==Verdadero, el tamaño del campo será tan grande como sea posible.
* Verdadero, se intentará que el tamaño del campo sea holgado, pero no más de lo necesario.
* **Falso.**

##### b. Los campos de tipo BOOLEAN no admiten el valor NULL:
* **Verdadero**
* Falso
* Depende de la implementación

##### c. Para añadir un campo a una tabla, se utiliza la sentencia ALTER TABLE:
* **Verdadero**
* Falso, se utiliza ADD
* Falso, se utiliza ADD FIELD

##### d. Los campos de un índice se ordenan automáticamente de forma ascendente:
* **Verdadero**
* Falso, se ordenan automáticamente de forma descendente.
* Falso, si son del tipo DATE, se ordenan automáticamente de forma descendente.

### 2. Elegir los tipos de datos más adecuados para los campos de la tabla representada en la figura 3.1 del libro.

```
NIF = VARCHAR (9)
Nombre = VARCHAR(20)
Apellidos = VARCHAR(20)
Telefono = NUMBER(9)
FechaNacimiento = DATE
FechaAlta = DATE

```


### 3. Escribir las sentencias CREATE TABLE correspondientes a las tablas representadas en la figura 3.8 del libro.


```SQL
CREATE Temp(
	empID NUMBER(4) PRIMARYKEY,
	Nombre VARCHAR(30),
	Apellido VARCHAR(30),
	Direc VARCHAR(70),
	nDept VARCHAR(15) REFERENCE deptID,
	FechaNac DATE
);

CREATE Tdept(
	deptID NUMBER(4) PRIMARYKEY,
	cNombre VARCHAR(30) NOT NULL
);
```


### 4. Escribir las sentencias ALTER TABLE que permiten eliminar la fecha de nacimiento, incluir el correo electrónico y ampliar en cinco caracteres la dirección de los empleados de las tablas resultantes del ejercicio anterior.


```SQL
ALTER TABLE empleado DROP COLUMN FechaNac,
ALTER TABLE empleado ADD email VARCHAR(250) NOT null,
ALTER TABLE empleado MODIFY Direc VARCHAR(255)
```


### 5. Escribe sentencia SQL con un índice sobre TSocio en la figura 4.5 del libro. Los campos del índice serán: fecha de alta, apellidos y nombre. Tiene que salir ordenado por la fecha de ata descendiente.



### 6. Escribir las sentencias CREATE TABLE de todas las tablas de la BD de la figura 3.28.

```SQL
CREATE TABLE TLibroTema (
nLibroID 
);

```

### 7. Escribir las sentencias ALTER TABLE necesarias para incluir en la tabla TAutor (ejercicio anterior) los campos dNacimiento y dFallecimiento.

```SQL
ALTER TABLE TAutor ADD dNacimiento DATE,
ALTER TABLE TAutor ADD dFallecimiento DATE
```
### 8. Diseña una base de datos que permita almacenar la información de una tienda online.

##### a. Tabla *productos*. Campos:
* Código del producto (`codigoPr`). Formato: 2 caracteres. Clave primaria.
* Descripción del producto (`descripcionPf`). Formato: 25 caracteres.
* Cantidad (`stock`). Formato: entero. La cantidad no puede ser negativa.
* Precio(precio). Formato: Número decimal con dos decimales (6 dígitos en total).

##### b. Tabla *clientes*. Campos:
* NIF (`NIF`). Formato: 9 caracteres. Clave primaria.
* Nombre (`nombre`). Formato: 15 caracteres. No puede ser nulo.
* Primer apellido (`apellido1`). Formato: 25 caracteres. No puede ser nulo.
* Segundo apellido (`apellido2`). Formato: 25 caracteres.

##### c. Tabla *pedidos*. Campos:
* Código de pedido (`codPed`). Formato: 3 caracteres. Clave primaria.
* NIF del cliente (`NIF`). Debe existir en la tabla productos.
* Código del producto (`codigoPr`). Debe existir en la tabla clientes.
* Cantidad de unidades compradas (`cantidad`). Formato: entero.

```SQL
CREATE TABLE productos (
	codigoPr CHAR(2) PRIMARY KEY,
	descripcionPf VARCHAR(25) NOT NULL,
	stock INT,
	precio NUMBER(6,2),
	CHECK(stock >= 0)
);

CREATE TABLE clientes (
	NIF CHAR(9) PRIMARY KEY,
	nombre VARCHAR(15) NOT NULL,
	apellido1 VARCHAR(25),
	apellido2 VARCHAR(25)
);

CREATE TABLE pedidos (
	codPed CHAR(3) PRIMARY KEY,
	NIF CHAR(9) REFERENCES clientes(NIF),
	codigoPr CHAR(2) REFERENCES productos(codigoPr),
	cantidad INT,
	CHECK (cantidad >= 0)
);

```