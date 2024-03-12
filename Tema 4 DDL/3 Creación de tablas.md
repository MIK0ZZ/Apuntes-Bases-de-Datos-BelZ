
La creación de tablas se realiza mediante la sentencia `CREATE TABLE`:

```SQL
CREATE TABLE nombreTabla(
	columna_1 tipo_1 [propiedades],
	columna_2 tipo_2 [propiedades],
	...
	columna_n tipo_n [propiedades],
	[restriccion integridad_1,
	...
	restriccion integridad_n]
);
```

Las propiedades de las columnas son:
* `DEFAULT valor`: valor por defecto cuando se inserta una nueva fila en la tabla.
* `NOT NULL`: si la columna no permite valores nulos (por defecto sí los permite).

Las restricciones son condiciones de **obligado cumplimiento** para una o más columnas de una tabla.

* Cuando afectan a una única columna las restricciones **pueden indicarse** en la definición de la columna.
* Si afectan a varias, se **deben** indicar al final de la definición de la tabla.
* Por defecto, Oracle asigna un nombre a cada restricción, pero se puede indicar el nombre: `[CONSTRAINT nombre] restricción`

[[4 Clave primaria y externa]]

