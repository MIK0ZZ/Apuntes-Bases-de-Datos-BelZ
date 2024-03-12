
La sentencia `INSERT` inserta una o varias filas nuevas en una tabla. La sintaxis básica para insertar una fila es:

`INSERT INTO tabla [(col_1. ..., col_k)] VALUES (val_1, ..., val_k);

* La lista de valores **debe** contener los valores a insertar.
* Los caracteres deben ir entre '' comillas simples. Por ejemplo:

`INSERT INTO client VALUES (21, 'MIKO', 'CODEX');`

* El orden de la lista de nombres de las columnas `col_1, ..., col_k` **debe coincidir** con el orden de la lista de valores `val_1, ..., val_k`.

* Si se omite la lista de nombres de columnas, se utiliza el **orden de definición** de las columnas en la creación de la tabla.

* Se puede utilizar una **sintaxis alternativa** con una consulta `SELECT` para generar las filas a insertar (se verá con detalle más adelante):

`INSERT INTO tabla_1 SELECT * FROM tabla_2:`

Donde `tabla_1` es la tabla en la que insertamos la información obtenida de la `tabla_2`.

