
Oracle intenta convertir datos **automáticamente** para que la expresión final tenga sentido.

Conversiones de texto a número y viceversa. Prueba los siguientes ejemplos:
`SELECT 5+ '3' FROM DUAL`
`SELECT 5 || '3' FROM DUAL`

Existen funciones de **conversión explícita**. Busca y prueba ejemplos sobre las siguientes funciones:
- `TO_NUMBER`: convierte a un string un número.
- `TO_CHAR`: convierte una fecha o un número a un string.
- `TO:DATE`: convierte un string a una fecha.