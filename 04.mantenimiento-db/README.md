- [Mantenimiento de los datos en la tabla](#mantenimiento-de-los-datos-en-la-tabla)
  - [Insertando registros en la tabla](#insertando-registros-en-la-tabla)
  - [Insertando varios registro en la tabla](#insertando-varios-registro-en-la-tabla)
  - [Alternando registros](#alternando-registros)
  - [Excluyendo registros](#excluyendo-registros)
  - [Incluyendo la clave primaria](#incluyendo-la-clave-primaria)
  - [Manipulando fecha y campos logicos](#manipulando-fecha-y-campos-logicos)
- [Ejercicios](#ejercicios)

# Mantenimiento de los datos en la tabla

<br>

## Insertando registros en la tabla

> Vamos a la base de dato correspondeite

```sql
    USE jugos;
```

Luego insertamos nuestro primer informacion

```sql
INSERT INTO tbproductos(
producto, nombre, envase, volumen, sabor, precio) VALUES ('773912', 'clean', 'botella pet', '1 litro', 'naranja', '8.01');
```

<br>

## Insertando varios registro en la tabla

Para insertar varios registro podemos copiar el mimo codigo y repetirlo las veces que necesites.

```sql
INSERT INTO tbproductos(
producto, nombre, envase, volumen, sabor, precio) VALUES ('838819', 'clean', 'botella pet', '1.5 litro', 'naranja', 12.01);

INSERT INTO tbproductos(
producto, nombre, envase, volumen, sabor, precio) VALUES ('1037797', 'clean', 'botella pet', '2 litro', 'naranja', 16.01);

INSERT INTO tbproductos(
producto, nombre, envase, volumen, sabor, precio) VALUES ('812829', 'clean', 'lata', '350ml', 'naranja', 2.81);
```

<br>

## Alternando registros

Para alterar el registro usamos `UPDATE` de la siguiente forma.

```sql
UPDATE tbproductos SET sabor = 'Lima/Limón', precio = 4.90
WHERE producto = '1041119';
```

Seleccionamos la tabla y con `SET` configuramos para luego seleccionar cada campo. <br>

`WHERE` utilizamos para encontrar el registro exacto.

<br>

## Excluyendo registros

Para poder eliminarlo utilizamos `DELETE`.

```sql
DELETE FROM tabla_de_vendedores WHERE NOMBRE='Joan Geraldo de la Fonseca';
```

Tenemos que tener cuidado porque podemos borrar informacion importantes, para eso se utiliza `WHERE` para darle un filtro.

<br>

## Incluyendo la clave primaria

Para poder incluir las llave primaria se lo realiza de la siguiente manera.

```sql
ALTER TABLE tbproductos ADD PRIMARY KEY(PRODUCTO);
```

En esta parte agregamos llave primaria para la tabla de productos.

> ¿Cuál es el propósito de incluir una clave primaria al momento de crear una tabla?
>
> - Garantizar la integridad de los datos.
> - Evitar la duplicidad en los registros.

<br>

## Manipulando fecha y campos logicos

Como no tenemos la columna de `FECHA` en nuestra tabla lo tenemos que crear de la siguiente manera.

```sql
ALTER TABLE tbclientes ADD COLUMN (FECHA_NACIMIENTO DATE);
```

En este caso vamos a crear un nuevo cliente y vamos agragarle la **FECHA** de nacimineto.

```sql
INSERT INTO tbclientes(
DNI ,
NOMBRE ,
DIRECCION1,
DIRECCION2 ,
BARRIO ,
CIUDAD ,
ESTADO ,
CP ,
EDAD ,
SEXO ,
LIMITE_CREDITO ,
VOLUMEN_COMPRA ,
PRIMERA_COMPRA ,
FECHA_NACIMIENTO) VALUES (
'456879548', 'Pedro el Escamoso', 'Calle del Sol, 25', '', 'Los Laureles', 'CDMX', 'Mexico', '65784', 55, 'M', 1000000, 2000, 0, '1971-05-25');
```

<br> <br>

# Ejercicios

> Vamos a incluir nuevos campos en la tabla de vendedores. Ellos serán la fecha de admisión. (Nombre del campo FECHA_ADMISION), y si el vendedor está o no de vacaciones. (Nombre del campo DE_VACACIONES). No olvides recrear la clave primaria y después incluye la siguiente información:

> - Matrícula - 00235
> - Nombre: Márcio Almeida Silva
> - Comision: 8%
> - Fecha de admisión: 15/08/2014
> - ¿Está de vacaciones? No

<hr>

> - Matrícula - 00236
> - Nombre: Cláudia Morais
> - Comision: 8%
> - Fecha de admisión: 17/09/2013
> - ¿Está de vacaciones? Si

<hr>

> - Matrícula - 00237
> - Nombre: Roberta Martins
> - Comision: 11%
> - Fecha de admisión: 18/03/2017
> - ¿Está de vacaciones? Si

<hr>

> - Matrícula - 00238
> - Nombre: Péricles Alves
> - Comision: 11%
> - Fecha de admisión: 21/08/2016
> - ¿Está de vacaciones? No

<br>

- Tips:
  - Elimina la tabla.
  - Crea la tabla nuevamente incluyendo los nuevos campos.
  - Crea la clave primaria.
  - Incluye los comandos de INSERT.

<details><summary><b>Solucion</b></summary>

```sql
DROP TABLE TABLA_DE_VENDEDORES;

CREATE TABLE TABLA_DE_VENDEDORES
( MATRICULA varchar(5),
NOMBE varchar(100),
PORCENTAJE_COMISION float,
FECHA_ADMISION date,
DE_VACACIONES bit);

ALTER TABLE TABLA_DE_VENDEDORES ADD PRIMARY KEY (MATRICULA);

INSERT INTO TABLA_DE_VENDEDORES
(MATRICULA, NOMBRE, FECHA_ADMISION, PORCENTAJE_COMISION, DE_VACACIONES) VALUES ('00235','Márcio Almeida Silva','2014-08-15',0.08,0);

INSERT INTO TABLA_DE_VENDEDORES
(MATRICULA, NOMBRE, FECHA_ADMISION, PORCENTAJE_COMISION, DE_VACACIONES) VALUES ('00236','Cláudia Morais','2013-09-17',0.08,1);

INSERT INTO TABLA_DE_VENDEDORES
(MATRICULA, NOMBRE, FECHA_ADMISION, PORCENTAJE_COMISION, DE_VACACIONES) VALUES ('00238','Pericles Alves','2016-08-21',0.11,0);

```

</details>
