
En SQL se pueden combinar los resultados de distintas sentencias `SELECT` utilizando los operadores de teoría de conjuntos. Consideremos los conjuntos A y B.

- `UNION`: se corresponde con la operación A u B.
- `INTERSECT`: se corresponde con la operación A n B.
- `MINUS`: se corresponde con la operación A-B o B-A.

```SQL
CREATE TABLE mitabla1 (
    c1 INTEGER
);
CREATE TABLE mitabla2 (
    c2 INTEGER
);

CREATE TABLE tabla3 (
  c3 INTEGER
);

INSERT INTO mitabla1 VALUES (1);
INSERT INTO mitabla1 VALUES (2);
INSERT INTO mitabla1 VALUES (3);

INSERT INTO mitabla2 VALUES (2);
INSERT INTO mitabla2 VALUES (3);
INSERT INTO mitabla2 VALUES (4);

INSERT INTO tabla3 VALUES(5);
INSERT INTO tabla3 VALUES(6);
INSERT INTO tabla3 VALUES(7);
```

> Ejercicio: Escribir que hace sin ejecutar el código.

```SQL
SELECT c1 FROM mitabla1 UNION SELECT c2 FROM mitabla2;
SELECT c1 FROM mitabla1 INTERSECT SELECT c2 FROM mitabla2;
SELECT c1 FROM mitabla1 MINUS SELECT c2 FROM mitabla2;


SELECT c1 FROM tabla1 UNION SELECT c2 FROM tabla2;
// {                              }
SELECT c1 FROM tabla1 INTERSECT SELECT c2 FROM tabla2;
// {                              }
SELECT c1 FROM tabla1 UNION SELECT c3 FROM tabla3;
// {
SELECT c2 FROM tabla2 MINUS SELECT c3 FROM tabla3;
// {                              }
SELECT c1 FROM tabla1 INTERSECT SELECT c2 FROM tabla2 INTERSECT SELECT c3 FROM tabla3;
// {
```