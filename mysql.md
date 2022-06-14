# BASE DE DATOS
## INDEX

[QUERYS](https://gguzmann.github.io/notas/querys.html)

Entrar a mysql por consola:

    mysql -u nameUser -p

Crear base de datos:
    
    create database nombre_database;

Mostrar bases de datos creadas:

    show databases;

Seleccionar o cambiar de base de datos:

    use nombre_database;

Mostrar tablas de base de datos:

    show tables;

Crear tablas

    create table nombre_tabla(
        nombre_columna1 tipo_dato(tamaño),
        nombre_columna2 tipo_dato(tamaño),
        ...
        PRIMARY KEY (nombre_columna1) 
        FOREIGN KEY (nombre_columna) REFERENCES nombre_tabla(colum_reference)
    );

Ejemplo:

    create table clientes(
        id int PRIMARY KEY NOT NUlL AUTOINCREMENT, // identificador unico / No puede ser nulo / si no agrega PK en insercion, crea una segun la anterior 
        nombre varchar(30) NOT NULL, // no puede ser nulo esta columna
        correo varchar(50),
        PRIMARY KEY (id) // identificador unico 
    );

Tipos de dato:

    String -> varchar(tamaño) // maximo 255
    Integer -> int(tamaño)


Ver estructura de tabla:

    describe nombre_tabla;

Vaciar datos de tabla:

    truncate table nombre_tabla; 

Eliminar tabla:

    drop table nombre_tabla;

Eliminar database:

    drop database nombre_database;

Agregar columna de tabla: 

    alter table nombre_tabla ADD nombre_columna tipo;

Eliminar columna de tabla: 

    alter table nombre_tabla DROP COLUMN nombre_columna;

## Comandos CRUD Mysql

    SELECT * FROM table         -> SELECCIONAR
    DELETE FROM table           -> ELIMINAR 
    INSERT INTO table VALUES    -> INSERTAR 
    UPDATE table SET            -> ACTUAlIZAR

Mostrar datos de tabla:

    select * from nombre_tabla; // selecciona todas las columnas de la tabla
    select column1, column2 from nombre_tabla; // seleccionar columna 1 y 2 de la tabla

Insertar datos en tabla:

    insert into nombre_tabla(colum1, colum2, ...) values(value1, value2, ...);

Actualizar dato en tabla:

    update nombre_tabla set colum1 = 'newValue', colum2 = 'newvalue', ...etc. where column = 'value' ;

Eliminar datos en tabla:

    delete from nombre_tabla where colum = 'value';


## CLAUSULAS

    WHERE       =    Seleciona solo la columna escogida
    AND         =    Concatenacion de clausulas
    LIMIT       =    Cantidad de datos a consultar
    ORDER BY    =    Orderna segun columna y puede ser asc o desc
    LIKE        =    '%a%' '%aon' 'a%'
    Between     =    Buscar numero entre 2 => where between 2 and 10

    // Operadores
    < > = != <= >=

Seleciona datos solo de la columna escogida:

    SELECT * FROM nombre_tabla WHERE colum = 'value';

Selecciona solo x cantidad de datos:

    SELECT * FROM nombre_tabla limit 5;

Ordena segun columna (asc, desc):

    SELECT * FROM nombre_tabla ORDER BY colum ASC;

# RELACIONES

**Relación uno a uno:** un vínculo entre la información de dos tablas, donde cada registro en cada tabla solo aparece una vez. Por ejemplo, puede haber una relación uno a uno entre los empleados y los coches que conducen.

**Relación de uno a muchos:** un registro de una tabla se puede asociar a uno o varios registros de otra tabla.. Por ejemplo, cada cliente puede tener varios pedidos de ventas.

**Relación de muchos a muchos:** se produce cuando varios registros de una tabla se asocian a varios registros de otra tabla. Por ejemplo, existe una relación de muchos a muchos entre los clientes y los productos. Se relacionan a traves de una tabla intermedio.


# PRIVILEGIOS

Crear Usuario localhost y dar permisos

    CREATE USER 'nameUser'@'localhost' IDENTIFIED BY 'Admin1234';
    GRANT ALL PRIVILEGES ON *.* TO 'nameUser'@'localhost' WITH GRANT OPTION;

Crear Usuario para conectarse remotanmente y dar permisos:
    
    CREATE USER 'nameUser'@'%' IDENTIFIED BY 'Admin1234';
    GRANT ALL PRIVILEGES ON *.* TO 'nameUser'@'%' WITH GRANT OPTION;

Actualizar privilegios:

    FLUSH PRIVILEGES;