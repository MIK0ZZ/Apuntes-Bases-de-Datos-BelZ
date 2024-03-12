
En SQL existen varios tipos de **reuniones de tablas**, de forma similar al álgebra relacional. las reuniones se especifican en la cláusula FROM:

- `tabla1 CROSS JOIN tabla2`
- `tabla1 NATURAL JOIN tabla2`
- `tabla1 JOIN tabla2 USING (col_1, ..., col_k)`
- `tabla1 JOIN tabla2 ON join_condition`
- `tabla1 LEFT OUTER JOIN tabla2 ON join condition`
- `tabla1 RIGHT OUTER JOIN tabla2 ON join condition`
- `tabla1 FULL OUTER JOIN tabla2 ON join condition`

Donde `join_condition` contiene las condiciones para combinar `tabla1` y `tabla2`.

- La condición de la cláusula `WHERE` puede contener nombres de columnas de las dos tablas.
- Si varias columnas tienen el mismo nombre, se puede utilizar `tabla.col` o alias de tablas (lo veremos un poco más adelante).
- varios `joins` pueden combinar más de dos tablas en la misma sentencia.

### Lista de JOINs:

[[9.1 CROSS JOIN]]:
- Hace una **multiplicación** de todas las filas de una tabla por todas las filas de otra tabla (y así sucesivamente). Esto quiere decir que si una tabla tiene 30 filas y otra 50 filas, entonces el resultado será de 1500 filas
- ![[Pasted image 20240301192829.png]]

[[9.2 NATURAL JOIN - JOIN USING]]:
- Relaciona las tablas **únicamente** con las columnas que tienen el **mismo nombre**.

[[9.3 JOIN ON]]:
- Es más explícito que el anterior. La diferencia se basa en el número de columnas devueltas. Esta cláusula también es llamada `INNER JOIN`
- ![[Pasted image 20240301192733.png]]

[[9.4 LEFT - RIGHT - FULL OUTER JOINS]]:
- Actúan de la misma manera que el `JOIN` regular.
- ![[Pasted image 20240301192746.png]]
- ![[Pasted image 20240301192805.png]]
- ![[Pasted image 20240301192813.png]]