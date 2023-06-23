- [SELECT una query de consult a un banco](#select-una-query-de-consult-a-un-banco)
  - [¿Cuáles son los principales comandos SQL?](#cuáles-son-los-principales-comandos-sql)
- [SQL y Modelado de base de datos](#sql-y-modelado-de-base-de-datos)
- [Instalando MySQL Server](#instalando-mysql-server)
    - [Lo que aprendimos en esta aula:](#lo-que-aprendimos-en-esta-aula)

# SELECT una query de consult a un banco

Imagine que tiene una tabla de base de datos, que realmente se puede hacer una analogía con una `Planilla de Excel` para guardar las informaciones de sus facturas:

<br>

| id  | titulo                      | pago       | valor |
| --- | --------------------------- | ---------- | ----- |
| 1   | bolígrafos                  | 2019-07-05 | 150   |
| 2   | notebook                    | 2019-07-01 | 1200  |
| 3   | macbook                     | 2019-07-02 | 2100  |
| 4   | micrófono                   | 2019-07-05 | 90    |
| 5   | matricula alura             | 2019-07-09 | 900   |
| 6   | gasolina reembolso director | 2019-06-10 | 200   |

<br>
Si quieres buscar todas las facturas que tengan valores superiores a mil pesos, la query que debes ejecutar es una que seleccionarás (SELECT) todos los campos (*) Dónde (WHERE) el valor de la factura sea superior a mil (valor > 1000):

<br>

    SELECT * FROM facturas WHERE valor > 1000

Y el resultado será algo como:

    mysql> SELECT * FROM facturas WHERE valor > 1000;

| id  | titulo   | pago       | valor |
| --- | -------- | ---------- | ----- |
| 2   | notebook | 2019-07-01 | 1200  |
| 3   | macbook  | 2019-07-02 | 2100  |

<br>

También podríamos enumerar todos los campos ordenados por fecha de pago, usando ORDER BY pago:

    mysql> SELECT * FROM facturas ORDER BY pago;

| id  | titulo                      | pago       | valor |
| --- | --------------------------- | ---------- | ----- |
| 6   | gasolina reembolso director | 2019-06-10 | 200   |
| 2   | notebook                    | 2019-07-01 | 1200  |
| 3   | macbook                     | 2019-07-02 | 2100  |
| 1   | bolígrafos                  | 2019-07-05 | 150   |
| 4   | micrófono                   | 2019-07-05 | 90    |
| 5   | matricula alura             | 2019-07-09 | 900   |

<br><br>

## ¿Cuáles son los principales comandos SQL?

Los comandos SQL principales son:

- `SELECT`: busca líneas en tablas de acuerdo con un criterio definido dentro de la denominada cláusula de WHERE
- `INSERT`: inserta nuevas líneas a la tabla. En nuestro caso, colocaría nuevas facturas dado los argumentos que se pasan al INSERT. Por ejemplo, en nuestro caso: INSERT INTO nf (título, pago, valor) VALUES 'bolígrafos', '2019-07-15', 150.
- `UPDATE`: actualiza líneas en la base de datos de acuerdo con un criterio de WHERE cómo cambiar el NIT
- `DELETE`: elimina líneas de la tabla según un criterio.

<br>

Todavía hay una infinidad de subcomandos para realizar búsquedas mejores y más elaboradas, como `JOIN`, `LIKE`, `HAVING` y `GROUP BY`

<br><br>

# SQL y Modelado de base de datos

Además de estos comandos, estarás expuesto a formas de crear tablas y columnas, como CREATE TABLE y ALTER TABLE. El `modelado de bases de datos` es la forma que definimos como las tablas almacenarán y se relacionarán nuestros datos, es decir, cómo estructurar estas relaciones para que no sea difícil de mantener y validar, como termina siendo con las planillas.

Por ejemplo, la tabla de arriba la creamos usando:

```sql
    CREATE TABLE facturas (
    id INT AUTO_INCREMENT,
    titulo VARCHAR(255) NOT NULL,
    pago DATE,
    valor DOUBLE,
    PRIMARY KEY (id)
    );
```

<br><br>

El acrónimo CRUD hace alusión a los estándares utilizados por el lenguaje SQL.

¿Qué quiere decir cada letra de este acrónimo?

`CREATE, READ, UPDATE y DELETE`

> ¡Alternativa correcta! Crear, leer, actualizar y eliminar son las funciones nativas de SQL.

<br><br>

# Instalando MySQL Server

Vamos a la pagina oficial y creamos una cuenta.

[Descargar MySQL](https://dev.mysql.com/downloads/workbench/)

Despues descarga los recursos necesario para seguir y te pide una contrasena root

<br><br>

### Lo que aprendimos en esta aula:

<br>

- Conocimos un poco sobre la historia de SQL como lenguaje de base de datos relacional.
- Vimos un poco sobre la historia y características de la base de datos MySQL.
- Aprendimos a instalar MySQL y Workbench.
