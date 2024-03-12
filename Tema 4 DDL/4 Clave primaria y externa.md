
Una PK se usa para identificar una fila. A veces, es necesario usar dos o más campos.
Determinar una buena PK es **crucial** para el diseño de la BD. Por ejemplo:

* Para identificar clientes puede ser suficiente con usar el NIF.
* Para identificar coches puede ser suficiente con la matrícula.
* Sin embargo, para identificar pedidos puede ser suficiente con:
	* El NIF del cliente y el código del producto (si solo puede realizar un pedido).
	* El NIF del cliente, el código y la fecha (si solo puede realizar un pedido al día).
	* También podríamos crear un código pedido (habría que pensar qué información utilizar).

La clave externa o foránea (FK) es un campo (o conjunto de campos) que son claves en otra tabla.

[[5 Tipos de restricciones en la creación de tablas]]