
* Añadir columnas a una tabla.
  `ALTER TABLE tabla ADD columna dominio [propiedades];`
  
* Eliminar columnas de una tabla.
  `ALTER TABLE tabla DROP COLUMN columna;`
  No se puede eliminar una columna que aparece en una restricción. En este caso se puede usar el siguiente comando.
  `ALTER TABLE tabla DROP columna CASCADE CONSTRAINTS;`

* Modificar columnas de una tabla (por ejemplo para extender el dominio).
  `ALTER TABLE tabla MODIFY (columna dominio [propiedades]);`
  
* Renombrar columnas de una tabla.
  `ALTER TABLE tabla RENAME COLUMN columna TO nuevoNombre;`

* Añadir restricciones a la tabla.
  `ALTER TABLE tabla ADD CONSTRAINT nombre tipo (columnas);`

* Eliminar restricciones de una tabla. La opción `CASCADE` hace que se eliminen las restricciones de integridad que dependen de la eliminada.
  `ALTER TABLE tabla DROP PRIMARY KEY;`
  `ALTER TABLE tabla DROP UNIQUE (campos);`
  `ALTER TABLE tabla DROP CONSTRAINT nombre [CASCADE];`

* Desactivar restricciones.
  `ALTER TABLE tabla DISABLE CONSTRAINT nombre [CASCADE]`

* Activar restricciones.
  `ALTER TABLE tabla ENABLE CONSTRAINT nombre;`

[[9 Más operaciones sobre las estructuras de las tablas.]]