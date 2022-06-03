# BASE DE DATOS

Entrar a mysql por consola:

    mysql -u nameUser -p

Crear base de datos:
    
    CREATE DATABASE ejemplo;

Mostrar bases de datos creadas:

    show databases;

Seleccionar o cambiar de base de datos:

    use ejemplo;

Mostrar tablas de base de datos:

    show tables;

Crear tablas

    create table nombre_tabla(
        nombre_columna1 tipo_dato(tamaño),
        nombre_columna2 tipo_dato(tamaño),
        ...
        PRIMARY KEY (nombre_columna1)    
    );

Ejemplo:

    create table clientes(
        id int,
        nombre varchar(30),
        correo varchar(50),
        PRIMARY KEY (id)
    );

Tipos de dato:

    String -> varchar(tamaño) // maximo 255
    Integer -> int(tamaño)


Ver estructura de tabla:

    describe nombre_tabla;

## PRIVILEGIOS

Crear Usuario localhost y dar permisos

    CREATE USER 'nameUser'@'localhost' IDENTIFIED BY 'Admin1234';
    GRANT ALL PRIVILEGES ON *.* TO 'nameUser'@'localhost' WITH GRANT OPTION;

Crear Usuario para conectarse remotanmente y dar permisos:
    
    CREATE USER 'nameUser'@'%' IDENTIFIED BY 'Admin1234';
    GRANT ALL PRIVILEGES ON *.* TO 'nameUser'@'%' WITH GRANT OPTION;

Actualizar privilegios:

    FLUSH PRIVILEGES;

Ejemplo:

    PK: Identificador unico en la tabla, de tipo numero generalmente

OJO: revisar app starUML.io