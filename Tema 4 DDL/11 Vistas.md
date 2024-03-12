
Una vista es una **tabla virtual**: una relación que no forma parte del modelo lógico pero que aparece como tal ante el usuario.

El Sistema Gestor de Bases de Datos (SGBD) solo guarda la definición de la vista, no el resultado, que se calcula cada vez que se utiliza.

A **casi** todos los efectos, una vista es como una tabla.

Cabe destacar que, por defecto, las vistas son actualizables: se modifican los datos de las tablas subyacentes (con restricciones).

Para definir una vista se utiliza la siguiente sintaxis.

`CREATE VIEW vista [(listaColumnas)] AS consulta [WITH READ ONLY | WITH CHECK OPTION];`

* `WITH READ ONLY`: la vista no permite modificaciones de los datos.
* `WITH CHECK OPTION`: permite la inserción y actualización de filas que cumplan la condición de la consulta.

Supongamos que queremos obtener los nombres de los empleados que trabajan para proyectos más horas que la media. Podemos resolverlo creando las siguientes vistas para la consulta.

* DNI y total de horas que trabaja cada empleado:
  `CREATE VIEW DNIHoras (DNI, Horas) AS`
  `SELECT DNI, SUM(Horas) FROM distribucion GROUP BY DNI;`

* Nombre y total de horas de cada empleado:
  `CREATE VIEW NombreHoras (Nombre, Horas) AS`
  `SELECT Nombre, Horas FROM Emp NATURAL JOIN DNIHoras;`

* Promedio de horas trabajadas por cada empleado:
  `CREATE VIEW MediaHoras (media) AS`
  `SELECT AVG(Horas) FROM NombreHoras;`

* La consulta final es la siguiente:
  `SELECT Nombre FROM NombreHoras WHERE Horas > (SELECT media FROM MediaHoras);`