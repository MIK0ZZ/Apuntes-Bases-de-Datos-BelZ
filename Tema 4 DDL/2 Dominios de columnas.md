A continuación, se recogen los tipos de datos más importantes.

* `CHAR(n)`: cadena de caracteres de longitud física *n*. Hasta 2000 caracteres, por defecto 1.

* `VARCHAR(n)`: cadenas de caracteres de longitud variable.

* `VARCHAR2(n)`: cadena de caracteres de longitud variable, máximo *n* (hasta 4000 caracteres). `VARCHAR` y `VARCHAR2` son sinónimos. La diferencia es únicamente la implementación.

* `NUMBER`: en el rango -10^125 hasta 10^125, con 38 dígitos significativos.

* `NUMBER(p, s)`: número de decimales, donde *p* es el número total de dígitos y *s* es el número de decimales.

* `INTEGER`: enteros de 32 bits.

* `DATE`: fecha y hora en una sola columna: año, mes, día, hora, minuto y segundo (y hasta milisegundos). Desde el 1 de enero del 4712 a.c, hasta el 31 de diciembre de 9999 d.c. El formato por defecto viene dado por el parámetro `NLS_DATE_FORMAT`. Internamente, una fecha se almacena como el número de días desde cierto punto de inicio. Se pueden realizar operaciones aritméticas.

| `'1-JAN-2001' + 10`         = | `'11-JAN-2001'` |
| ---- | ---- |
| `'27-FEB-2000' + 2`         =  | `'29-FEB-2000'` |
| `'10-MAY-2000' - 1-MAY-2000` =  | `9` |
Oracle dispone de más tipos de datos que puedes consultar en el siguiente enlace.

