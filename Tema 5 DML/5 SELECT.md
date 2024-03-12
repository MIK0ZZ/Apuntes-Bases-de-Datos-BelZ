Las consultas de datos se hacen mediante la sentencia `SELECT`. Su sintaxis básica es la siguiente:

```SQL
SELECT columna_1, ..., columna_r FROM tabla_1, ..., tabla_k
WHERE condición
ORDER BY criterio
```

* ¿Qué quiero leer?: `columna_1, ..., columna_r`
* ¿De dónde quiero leerlo?: `tabla_1, ..., tabla_k`
* ¿Cómo quiero filtrar los resultados?: `condición`
* ¿Cómo quiero ordenar el resultado y en función de qué campo se va a realizar dicha ordenación?: `criterio`

* La cláusula `SELECT` especifica las columnas que deben aparecer en el resultado.
* La cláusula `FROM` especifica las tablas de las que obtiene la consulta.
* La cláusula `WHERE` es opcional y especifica las condiciones de selección. Si no se incluye, entonces se seleccionan todas las filas.
* La cláusula `ORDER BY` es opcional y especifica el criterio de ordenación de las filas obtenidas.
* La cláusula `LIKE` se usa para encontrar cosas específicas. Se debe poner % para lo que no se busca (Mirar práctica 5 ej4 apartado f).

Consideremos la siguiente tabla llamada `Distribución`:
![[Pasted image 20240214195312.png]]

Seleccionar los códigos de los proyectos del empleado con DNI `27347234T`:

`SELECT codigoPr FROM Distribución WHERE DNI = '27347234T';`

Seleccionar los DNI de los empleados que trabajan entre 15 y 25 horas en algún proyecto junto con las horas y el código de ese proyecto:

`SELECT codigoPr, DNI, horas FROM Distribucion WHERE horas >= 15 AND horas <= 25;`

Las consultas SQL trabajan con **multiconjuntos** en lugar de conjuntos. Es decir, se pueden repetir valores. La consulta anterior mostraría este resultado:
![[Pasted image 20240214195616.png]]

Para trabajar con conjuntos (eliminando tuplas duplicadas) se utiliza la cláusula `DISTINCT`:

`SELECT DISTINC DNI FROM Distribucion WHERE horas > 20;`
![[Pasted image 20240214195728.png]]

Para seleccionar todas las columnas de las tablas incluidas en la cláusula `FROM` se utiliza `*`:
`SELECT * FROM Distribucion WHERE horas > 20;`

Se pueden cambiar el nombre de las columnas en el resultado;
`SELECT DNI "DNI del empleado" FROM Distribución;`

En algunos casos necesitamos ejecutar una consulta que **no requiere ninguna tabla**.
Podemos usar una tabla especial `DUAL` para evaluar expresiones (veremos ejemplos más adelante cuando estudiemos las funciones).
`SELECT SYSDATE, 2*3, SQRT(2) FROM DUAL;`

[[5.1 Evaluación de una consulta]]
[[5.2 Condición de la cláusula WHERE]]
[[5.3 Ordenación de resultados]]
