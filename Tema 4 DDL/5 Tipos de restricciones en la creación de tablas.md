
Se consideran los siguientes tipos de restricciones (los nombres de las columnas solo son necesarios para las restricciones de varias columnas).

* `PRIMARY KEY [C1, ..., Cj]`: la tabla no permite valores duplicados para `C1, ..., Cj` y tampoco pueden contener valores nulos.
* `UNIQUE [C1, ..., Cj]`: la tabla no permite valores duplicados para `C1, ..., Cj`.
* `FOREIGN KEY [C1, ..., Cj] REFERENCES tabla [B1, ..., Bj]`: los valores `C1, ..., Cj` de cualquier fila **deben ser null** o **deben corresponder** al valor de la PK (o restricción `UNIQUE`) de una fila de la `tabla`.
* `CHECK (condition)`: la expresión booleana "condition" debe ser cierta para todas las filas de la tabla.

Aquí podemos ver algunos ejemplos. Observa cómo nombramos a las restricciones (podríamos activar/desactivar cada restricción desde Oracle).

```SQL
CREATE TABLE sucursal (
	nombre sucursal VARCHAR(15) PRIMARY KEY,
	ciudad CHAR(20) NOT NULL CONSTRAINT cl_UK UNIQUE,
	activos NUMBER(12,2 DEFAULT 0)
);

CREATE TABLE cliente(
	dni VARCHAR(9) NOT NULL,
	nombre cliente CHAR(35) NOT NULL,
	domicilio CHAR(50) NOT NULL,
	CONSTRAINT cl_PK PRIMARY KEY (dni)
);
```

```SQL
CREATE TABLE cuenta(
	numero cuenta CHAR(20) PRIMARY KEY,
	nombre sucursal VARCHAR(15) REFERENCES sucursal,
	saldo NUMBER(12,2) DEFAULT 100,
	CHECK (saldo >= 100)
);

CREATE TABLE impositor(
	dni VARCHAR2(9) REFERENCES cliente,
	numero cuenta CHAR(20) NOT NULL,
	PRIMARY KEY (dni, numero cuenta),
	FOREIGN KEY (numero cuenta) REFERENCES cuenta
	
);
```

