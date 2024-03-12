
### 1. ¿Qué es DDL, para qué se utiliza y qué tipo de operaciones puedes hacer con él?

DLL sirve para la creación de tablas, índices, modifciación de tablas, etc.

### 2. ¿Qué son las restricciones de integridad y para qué se utilizan? Escribe, al menos, cuatro ejemplos de restricciones en su contexto y explica qué hace cada una de ellas.

Las restricciones de integridad son formas de garantizar el cumplimiento de ciertas normas.

1. PRIMARY KEY: La tabla no permite valores duplicados ni nulos
2. UNIQUE: La tabla no permite valores duplicados
3. FOREIGN KEY: Los valores clave de cualquier fila deben ser null o corresponder al valor de la Primary Key
4. CHECK (`condition`): La expresión `condition` debe ser cierta para todas las filas de la tabla.

### 3. Explica con tus palabras los ejemplos ALTER TABLE que aparecen en la diapositiva 17 del tema de DDL.

1. ADD columna: Pues añade una columna a una tabla ^^
2. DROP COLUMN columna: Elimina una columna de una tabla (No se puede eliminar una que aparezca en una restricción)
3. MODIFY: Modifica una columna de una tabla (no el contenido, sino sus propiedades)
4. RENAME COLUMN: Renombra la columna
5. ADD CONSTRAINT: Añade restricciones a una tabla como una Primary Key o Unique, etc...
6. DISABLE CONSTRAINT: Desactiva restricciones
7. ENABLE CONSTRAINT: Activa restricciones

### 4. ¿Qué son las tablas *hash* y para qué sirven? Nombra algunas de sus características.

Es una tabla donde se guardan todos los registros de una base de datos.
La implementación de una tabla hash está basada en los siguientes elementos:

Una tabla de un tamaño razonable para almacenar los pares (clave, valor).

Una función “hash” que recibe la clave y devuelve un índice para acceder a una posición de la tabla.

Un procedimiento para tratar los casos en los que la función anterior devuelve el mismo índice para dos claves distintas. Esta situación se conoce con el nombre de colisión.

### 5. Una compañía de coches de segunda mano necesita vuestra ayuda para diseñar la base de datos. Se considera relevante almacenar la información de las oficinas (tabla oficinas), la de los vendedores (tabla vendedores), la de los clientes (tabla clientes), la de los modelos de los coches vendidos (tabla modelos) y la de las ventas (tabla ventas). Estas son las especificaciones de las tablas de la base de datos:

##### a. oficinas: código de oficina, dirección y provincia.
##### b. vendedores: NIF del vendedor, su nombre y la oficina a la que pertenece.
##### c. clientes: NIF del cliente y su nombre.
##### d. modelos: marca, modelo y precio de cada coche.
##### e. ventas: NIF del vendedor, NIF de cliente, marca y modelo del coche, fecha de la venta e importe de la venta.

#### Crea las tablas con los tipos de datos y las restricciones de integridad adecuadas para representar la información anterior. Considera establecer un formato de fecha válido antes de hacer uso del tipo de datos DATE en la tabla ventas: alter session set NLS_DATE_FORMAT = ‘DD-MM-YYYY’;

```SQL
CREATE TABLE oficinas (
	
);
CREATE TABLE vendedores (
	VARCHAR 10 PRIMARY KEY,
);
```
