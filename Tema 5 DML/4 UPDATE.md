
La sentencia `UPDATE` modifica los valores de las filas existentes en una tabla que cumplan una determinada condición. La sintaxis es la siguiente:

`UPDATE tabla SET col_1 = expr_1, ... col_k = expr_k WHERE condición;`

* La condición de la cláusula `WHERE` se evalúa para **cada fila**. Si es *true*, se modifican las columnas especificadas en la cláusula `SET`.
* Si no se especifica la cláusula `WHERE`, se actualizan **todas las filas** de la tabla.

La cláusula `WHERE` puede contener condiciones complejas, incluso otras consultas **anidadas**. Veamos dos ejemplos más;

`UPDATE empleado SET sueldo = sueldo*1.1 WHERE dept_ID = '0001';`

`UPDATE account SET balance = balance*1.03, comission = 0.25 WHERE empresa_id = 'QPL-IUE-982';`

[[5 SELECT]]