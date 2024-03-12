
Los índices permiten **acelerar** las operaciones de consulta y ordenación sobre los campos a los que el índice hace referencia (internamente se representan mediante árboles B o tablas *hash*). Sin embargo, hacen menos eficientes las operaciones de modificación de datos (UPDATE, INSERT).

La mayoría de los índices se crean de manera automática como consecuencia de las restricciones `PRIMARY KEY` y `UNIQUE`.

Se pueden crear índices adicionales para aquellas combinaciones de columnas sobre las que se realizarán búsquedas e instrucciones de ordenación frecuentemente.

`CREATE [UNIQUE] INDEX nombreIndice ON nombreTabla(columna_1, ..., columna_n);`

Por ejemplo, puede ser conveniente crear índices sobre las claves externas si se espera que se realicen consultas sobre esas combinaciones de columnas.

En cualquier caso, la creación de índices es tarea del **administrador** de la BD.

[[11 Vistas]]