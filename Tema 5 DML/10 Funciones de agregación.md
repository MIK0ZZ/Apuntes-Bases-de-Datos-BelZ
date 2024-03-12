
En SQL también se puede realizar consultas en las que se agrupan las filas resultado.

Las funciones de agregación permiten calcular estos resultados sobre grupos de filas de una consulta `SELECT`:
- `COUNT([DISTINCT] column|expre)`: devuelve el número de valores de la columna column o la expresión expre. No incluye filas con valor `NULL`.
- `SUM([DISTINCT] column\expre)`: devuelve la suma de todos los valores de la columna column (numérica) o la expresión expre.
- `AVG([DISTINCT] column|expre)`: calcula el valor medio de todos los valores de la columna col‎umn (numérica) o la expresión expre.
- `MAX(column|expre)`: devuelve el valor máximo de la columna o expresión.
- `MIN(column|expre)`: devuelve el valor mínimo de la columna o expresión.

Se puede utilizar `COUNT (*)` para contar todas las filas, incluyendo duplicados y nulos.