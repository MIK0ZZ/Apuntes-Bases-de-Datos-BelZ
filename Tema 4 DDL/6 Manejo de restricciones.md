
Cuando se insertan o modifican filas de una tabla, se **debe garantizar el cumplimiento de las restricciones de clave externa**:
* Cuando se **modifica** la PK (o única) de una fila a la que se refiere la FK de otra tabla.
* Cuando se **elimina** una fila de una tabla a la que se refiere una FK de otra tabla.

Si se incumple una FK se rechaza la acción y produce error. Si el diseño lo requiere, se puede modificar este comportamiento mediante cláusulas en la creación de la FK:
* `ON DELETE CASCADE`: cuando se elimina una fila de la tabla referida, todas las filas a la que referencia también son eliminadas.
* `ON DELETE SET NULL | SET DEFAULT`: las columnas que referencia una fila eliminada se actualizan a `NULL` o sus valores por defecto.

Observa a qué campos afectan las restricciones. [[5 Tipos de restricciones en la creación de tablas]]

```SQL
CREATE TABLE cuenta(
	numero cuenta CHAR(20) PRIMARY KEY,
	nombre sucursal CHAR(15) REFERENCES sucursal ON DELETE SET NULL,
	saldo NUMBER(12,2) DEFAULT 100,
	CHECK(saldo >= 100)
);

CREATE TABLE impositor(
	dni VARCHAR2(9) REFERENCES cliente ON DELETE CASCADE,
	numero cuenta CHAR(20) NOT NULL,
	PRIMARY KEY (dni, numero cuenta),
	FOREIGN KEY (numero cuenta) REFERENCES cuenta ON DELETE CASCADE
	
);
```