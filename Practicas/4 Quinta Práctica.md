### 1. Realiza las siguientes inserciones. No todas son válidas. Determina la razón por la cual algunas de ellas son inválidas.

```SQL
INSERT INTO clientes VALUES ('1111','Juan','Garcia','Perez');
INSERT INTO clientes VALUES ('2222','Pedro','Garcia','Perez');
INSERT INTO clientes VALUES ('3333','Ana','Garcia','Perez');
INSERT INTO clientes VALUES ('4444','Juan','Garcia','Perez');
INSERT INTO clientes VALUES ('1111','Patricia','Garcia','Perez'); /*1111 ya existe*/

INSERT INTO productos VALUES ('01','xxxx',23,6.35);
INSERT INTO productos VALUES ('02','tomates',30,4.15);
INSERT INTO productos VALUES ('03','patatas',21,0.33);
INSERT INTO productos VALUES ('04','peras',22,6.85);
INSERT INTO productos VALUES ('05','melones',260,10.35);
INSERT INTO productos VALUES ('06','sandías',210,7.35);
INSERT INTO productos VALUES ('07','tomates',200,6.359);

INSERT INTO pedidos VALUES ('01','1111','01',3);
INSERT INTO pedidos VALUES ('02','2222','02',3);
INSERT INTO pedidos VALUES ('03','3333','02',3);
INSERT INTO pedidos VALUES ('04','1111','01',3);
INSERT INTO pedidos VALUES ('05','1111','01',3);
INSERT INTO pedidos VALUES ('06','4444','01',3);
INSERT INTO pedidos VALUES ('07','5555','01',3); /*No existe 5555*/
INSERT INTO pedidos VALUES ('08','1111','05',3); 
INSERT INTO pedidos VALUES ('09','1111','05',3); 
INSERT INTO pedidos VALUES ('10','3333','01',3); 
INSERT INTO pedidos VALUES ('11','3333','07',3);
INSERT INTO pedidos VALUES ('12','1111','01',3);
INSERT INTO pedidos VALUES ('13','1111','08',3); /*No existe 08*/
INSERT INTO pedidos VALUES ('14','4444','01',3);
INSERT INTO pedidos VALUES ('15','1111','01',3);
INSERT INTO pedidos VALUES ('16','1111','01',3);

```
### 2. Comprueba lo que hay dentro de cada tabla. Haz tres consultas para mostrar el contenido de las tres tablas y el de todos sus campos.

```SQL
SELECT codigoPr, descripcionPf, stock, precio FROM productos;
SELECT NIF, nombre, apellido1, apellido2 FROM clientes;
SELECT codPed, NIF, codigoPr, cantidad FROM pedidos;
/*Se podría haber hecho con asterisco y ya xd*/
```

### 3. Se han detectado los siguientes registros incorrectos. Realiza las operaciones oportunas para arreglarlo.
#### a. La descripción del producto con código 01 es incorrecta. Descripción correcta: huevos.
```sql
UPDATE productos SET descripcionPf = 'huevos' WHERE codigoPr = 01;
```
#### b. Los tomates aparecen en la tabla producto dos veces. Elimina la aparición con código 07. Date cuenta que las apariciones en pedidos con codPed 07 deberían tener el código 02.

```sql
UPDATE pedidos SET codigoPr = 02 WHERE codigoPr = 07;
DELETE FROM productos WHERE codigoPr = 07;
```
#### c. En clientes añade el campo edad (adivina el tipo). Además, los apellidos están mal. Los datos correctos son los siguientes:

1. **Pedro García Perez, edad: 30**
2. **Juan González García, edad: 45**
3. **Ana García García, edad: 22**
4. **Juan Pérez Gómez, edad: 55**

```sql
ALTER TABLE clientes ADD edad INT;
UPDATE clientes SET edad = 45, nombre = 'Juan', apellido1 = 'González', apellido2 = 'García' WHERE NIF = '1111';

UPDATE clientes SET edad = 30, nombre = 'Pedro', apellido1 = 'García', apellido2 = 'Perez' WHERE NIF = '2222';

UPDATE clientes SET edad = 22, nombre = 'Ana', apellido1 = 'García', apellido2 = 'García' WHERE NIF = '3333';

UPDATE clientes SET edad = 55, nombre = 'Juan', apellido1 = 'Perez', apellido2 = 'Gomez' WHERE NIF = '4444';
```

### 4. Diseña las siguientes consultas:
#### a. Todos los productos (su descripción) para los que haya más de 100 unidades.
```sql
SELECT descripcionPr FROM productos WHERE stock > 100;
```
#### b. Todos los productos (su código) cuyo precio esté entre 5 y 10 euros.
```sql
SELECT codigoPr FROM productos WHERE precio > 5 && producto < 10;
```
#### c. Todos los productos (su descripción) para los que haya más de 200 unidades y cuesten menos de 10 euros.
```sql
SELECT descripcionPr FROM productos WHERE stock > 200 && precio < 10;
```
#### d. Todos los nombres de los clientes cuyo primer apellido sea García.
```sql
SELECT nombre FROM clientes WHERE apellido1 = 'Garcia';
```
#### e. Todos los nombres de los clientes cuyos apellidos sean iguales.
```sql
SELECT nombre FROM clientes WHERE apellido1 = apellido2;
```
#### f. Todos los nombres de los clientes cuyo primer apellido acabe en ez.
```sql
SELECT nombre FROM clientes WHERE apellido1 LIKE '%ez';
```
#### g. Todos los NIFs de los clientes (sin repeticiones) que hayan hecho algún pedido.
```sql
SELECT DISTINCT NIF FROM pedidos ; /*No hace falta el where porque para estar en la tabla ha tenido que hacer al menos algún pedido*/
```
### 5. Sube el precio un 20% de los productos con un stock menor que 100.

```sql
UPDATE productos SET precio += (precio*20/100) WHERE stock < 100;
```
### 6. Crea una tabla llamada pedidos1111 que contenga los campos de pedidos con excepción de nif (con la misma estructura que pedidos) de tal manera que contenga todos los pedidos que haya realizado el cliente con NIF 1111. Restricción: se debe realizar con solo dos instrucciones; una para crear la tabla y otra para hacer el insert.

```sql
CREATE TABLE pedidos1111 (
	codPed CHAR(3) PRIMARY KEY,
	codigoPr CHAR(2) REFERENCES productos(codigoPr),
	cantidad INT,
	CHECK (cantidad >= 0)
);

INSERT INTO pedidos1111 SELECT * FROM pedidos WHERE NIF = '1111';
```

