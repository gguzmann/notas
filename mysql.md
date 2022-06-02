# BASE DE DATOS

Entrar a mysql por consola:

    mysql -u nameUser -p

Crear Usuario localhost y dar permisos

    CREATE USER 'nameUser'@'localhost' IDENTIFIED BY 'Admin1234*';
    GRANT ALL PRIVILEGES ON *.* TO 'nameUser'@'localhost' WITH GRANT OPTION;

Crear Usuario en la nube? y dar permisos
    
    CREATE USER 'nameUser'@'%' IDENTIFIED BY 'Admin1234*';
    GRANT ALL PRIVILEGES ON *.* TO 'nameUser'@'%' WITH GRANT OPTION;

    FLUSH PRIVILEGES;


Crear base de datos:
    
    CREATE DATABASE 'name_DB';

