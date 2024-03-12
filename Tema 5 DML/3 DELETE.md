
La sentencia `DELETE` elimina filas existentes en una tabla que cumplan una determinada **condición**. La sintaxis es al siguiente:

`DELETE FROM tabla WHERE condición;`

* La condición de la cláusula `WHERE` se evalúa para **cada fila**. Si es *true*, se elimina a fila
* La cláusula `WHERE` es opcional. Si se omite, se borran **todas las filas** de la tabla. !!!!
* La cláusula `WHERE` puede contener condiciones complejas e incluso otras consultas **anidadas** (lo veremos más adelante). Veamos un ejemplo:

`DELETE FROM cliente WHERE id_cliente = 37;`

[[4 UPDATE]]