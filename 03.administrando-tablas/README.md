### Administrando las tablas de la base de datos

---

- [Tipo de datos](#tipo-de-datos)
  - [Creando tablas](#creando-tablas)
  - [Atributos de los campor numericos](#atributos-de-los-campor-numericos)
    - [Fecha y hora](#fecha-y-hora)
    - [String](#string)
    - [Atributos de los campos string](#atributos-de-los-campos-string)
    - [Campos espaciales (_GPS_)](#campos-espaciales-gps)
  - [Eliminar tabla](#eliminar-tabla)
- [Ejercicio](#ejercicio)
    - [EMPRESA DE JUGO](#empresa-de-jugo)

<br>

# Tipo de datos

<h3><strong>Lo que aprenderemos en esta aula:</strong></h3>

- Los tipos de datos que componen una tabla.

- A crear una tabla, tanto por líneas de comando como por el asistente.

- A eliminar una tabla.

<br>

## Creando tablas

<br>

> **Numero enteros**

| Tipo      | Valor en Bytes | Menor valor (signed) | Menor valor (unsigned\*) | Menor valor (signed) | Mayor valor(unsigned) |
| --------- | -------------- | -------------------- | ------------------------ | -------------------- | --------------------- |
| TINYINT   | 1              | -128                 | 0                        | 127                  | 255                   |
| SMALLINT  | 2              | -32768               | 0                        | 32767                | 65535                 |
| MEDIUMINT | 3              | -8388608             | 0                        | 8388607              | 16777215              |
| INT       | 4              | -2147483648          | 0                        | 2147483647           | 47483647              |
| BIGINT    | 8              | -2E63                | 0                        | 2E63(-1)             | 2E63                  |

\*unsigned: Sin signo(+/-)

<br>

> **Numero decimales**

| Tipo     | Precision en Bytes | Tipo   |
| -------- | ------------------ | ------ |
| FLOAT\*  | 4                  | Simple |
| DOUBLE\* | 8                  | Doble  |

\*coma flotante

Ej. Si declaramos un FLOAT (6,4) e incluimos el numero 76.00009 el valor almacenado sera 76.00001

| Tipo              | Cantidad de digitos |
| ----------------- | ------------------- |
| DECIMAL O NUMERIC | 65                  |

Es un numero fijo, si declaramos DECIMAL(5,3) solo pondremos alacenar desde -99.999 hasta 99.999

> **Bit**

| Tipo | Cantidad de digitos |
| ---- | ------------------- |
| Bit  | 65                  |

Ej. BIT(1) puede ser 0 o 1
Bit(3) puede ser 000,001 010,0011,100,101,110,111

<br>

## Atributos de los campor numericos

<br>

> `SIGNED o UNSIGNED:` Con signo o sin signo.

> `ZEROFILL:` Llena los espacios con cero. Ej. INT(5); si alacenamos 54, el campo va a quedar 00054.

> `AUTO_INCREMENT:` Hay un incremento secuencual Ej. 1,2,3,4,5..

> `OUT OF RANGE:` Es un error que se presenta cuando los valores se salen de los limites.

<br>

### Fecha y hora

<br>

> `DATE:` 1000-01-01 hasta 9999-12-31

> `DATETIME:` 1000-01-01 00:00:00 hasta 9999-12-31 23:59:59.

> `TIMESTAMP:` 1970-01-01 00:00:01 UTC hasta 2038-01-19 UTC

> `TIME:` -838:58:59 y 839:59:59

> `YEAR:` 1901 hasta 2155 (puede expresarse en formato de 2 0 4 digitos)

  <br>

### String

<br>

> `CHAR:` Cadena de caracteres como valor fijo de 0 a 255. Ej CHAR(4) = "aa" -> "..aa"

> `VARCHAR:` Cadena de caracteres como valor variable de 0 a 255 Ej. VARCHAR(4)= "aa" -> "aa"

> `BINARY:` Cadena de caracteres como valor fijo de 0 a 255. (Con numero binarios - bit)

> `VARBINARY:` Cadena de caracteres como valor fijo de 0 a 255. (Con numero binarios - bit)

> `BLOB:` Binarios largos -> TINYBLOB, MEDIUMBLOB, LONGBLOB.

> `TEXT:` Binarios largos -> TINYTEXT, MEDIUMTEXT, LONGTEXT.

> `ENUM:` Definimos opciones en una lista predefinida -> Talla ENUM('pequeno', 'medio, 'grande')

  <br>

### Atributos de los campos string

<br>

> `SET y COLLATE:` El tipo de conjunto de caracteres que va a aceptar -> uft-8, uft-16...

  <br>

### Campos espaciales (_GPS_)

<br>

> `POINT` -> Punto

> `GEOMETRY` -> Area

> `LINESTRING` -> Linea

> `POLYGON` -> Area

<br>

## Eliminar tabla

Eliminar la tabla `TABLA_DE_VENDEDORES2` usando script SQL.

Para crear la tabla antes de eliminarla, ejecute:

```sql
CREATE TABLE TABLA_DE_VENDEDORES2 (
    MATRICULA varchar(5),
    NOMBRE varchar(100),
    PORCENTAJE_COMISION float);
```

Después de crear la tabla conforme al enunciado, elimínala utilizando el comando:

```sql
DROP TABLE TABLA_DE_VENDEDORES2;
```

<br>
<br>

# Ejercicio

<br>

### EMPRESA DE JUGO

1. Crea una tabla para registrar a cada cliente.

Conversando con las personas en el area de registro de clientes, nos dice que la informacion mas importante para el cliente es DNI, nombre completo, direccio, edad, sexo, limite de credito, volumen minimo de jugo que puede comprar y si ya hizo la primera compra.

<details><summary><b>Solucion</b></summary>
<p>

**Hacemos una lista con los datos**

```
Registro de clientes

DNI
NOMBRE COMPLETO
DIRECCION1
DIRECCION2
BARRIO
CIUDAD
ESTADO
COMPLETOEDAD
SEXO
LIMITE_CREDITO (para compra)
VOLUMEN_COMPRA ( minimo de compra)
PRIMERA_COMPRA (ya la realizo)
```

**Lo pasamos a codigo SQL**

```sql
  USE jugos;
  CREATE TABLE TBCLIENTES(
    DNI VARCHAR(20),
    NOMBRE VARCHAR(150),
    DIRECCION1 VARCHAR(150),
    DIRECCION2 VARCHAR(150),
    BARRIO VARCHAR(50),
    CIUDAD VARCHAR(50),
    ESTADO VARCHAR(50),
    CP VARCHAR(10),
    EDAD SMALLINT,
    SEXO VARCHAR(1),
    LIMITE_CREDITO FLOAT,
    VOLUMEN_COMPRA FLOAT,
    PRIMERA_COMPRA BIT(1)
  );
```

</p>
</details>

<br>

2. Crea una tabla para registrar los productos.

A los clients les vamos a vender productos.
En la tabla de productos tendremos los jugos de fruta que vendemos en la empresa. Habando con los usuarios de la empresa, me presentaron los campos de codigo de producto, nombre del producto, envase, tamano, asboir y precio de lista.

<details><summary><b>Solucion</b></summary>
<p>

```
REGISTRO DE PRODUCTOS

PRODUCTO
NOMBRE
ENVASE
VOLUMEN
SABOR
PRECIO

```

**Lo pasamos a codigo SQL**

```sql
  USE jugos;
  CREATE TABLE `jugos`.`TBPRODUCTOS`(
    PRODUCTO VARCHAR(20),
    NOMBRE VARCHAR(150),
    ENVASE VARCHAR(50),
    VOLUMEN VARCHAR(20),
    SABOR VARCHAR(50),
    PRECIO FLOAT
  );
```

</p>
</details>

<br>

3. Nuestro sistema de ventas solicita la creación de una tabla más para los vendedores.

<br>

**Información importante:**

- El nombre de la tabla debe ser TABLA_DE_VENDEDORES.

- El vendedor tiene el número interno de la matrícula, que será almacenado en el campo MATRÍCULA, que debe ser un string de 5 posiciones.

- El nombre del vendedor deberá ser almacenado en el campo NOMBRE, y debe ser un string de 100 posiciones.

- Crear el campo PORCENTAJE_COMISION que representa el porcentaje de comisión que el vendedor gana sobre cada venta.

- Crear esta tabla en la base de datos jugos.

<details><summary><b>Solucion</b></summary>
<p>

```
REGISTRO DE PRODUCTOS

PRODUCTO
NOMBRE
ENVASE
VOLUMEN
SABOR
PRECIO

```

**Lo pasamos a codigo SQL**

```sql
  CREATE TABLE TABLA_DE_VENDEDORES (
    MATRICULA varchar(5),
    NOMBRE varchar(100),
    PORCENTAJE_COMISION float);
```

</p>
</details>
