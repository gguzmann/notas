# QUERYS SQL

## SELECT
SELECT -> seleciona los datos de una tabla que uno quiera

    query   parametros  tabla      alias;
    SELECT   *  FROM    customers  c;

Obtener clientes con nombre que contenga 'toy' en nombre:

    SELECT *                                Seleccionar todas las columnas (*)                         
    FROM customers c                        de tabla customers(alias c)
    WHERE c.customersName LIKE '%toy%';     donde(where) columna customersName contiene(like) 'toy';

Obtener nombre y numero de clientes que contengan 'toy' en nombre:

    Seleccionar columnas customerName y customerNumber(c.customerName, c.customerNumber) 
    de tabla customers(alias c) 
    donde(where) columna customersName contiene(like) 'toy';

    select c.customerName, c.customerNumber
    from customers c 
    where c.customerName like '%toy%';

Obtener nombre, numero y ciudad de clientes que sean de 'Madrid':

    Seleccionar columnas customerName, customerNumber y city(c.customerName, c.customerNumber, c.city)
    de tabla customers(alias c) 
    donde(where) columna city es igual a 'Madrid';

    select c.customerName, c.customerNumber, c.city 
    from customers c 
    where c.city = 'Madrid';

## NO HACER:
Obtener todo el registro de ambas tablas repetidamente.
    select * from customers c, orders o;


Obtener todas las ordenes del cliente 496: 

    SELECT c.customerName, c.customerNumber, o.orderNumber from customers c, orders o where c.customerNumber = o.customerNumber and c.customerNumber = 496 ORDER BY c.customerNumber desc; 

## JOIN 'S

INNER JOIN:

Obtener todos los clientes y ordenes que tengan la misma ID(customerNumber):

    Seleccionar todas las columnas(*)
    de tabla customer(alias: c)
    unida a tabla orders(inner join)(o)
    en donde(ON) c.customerNumber es igual a o.customerNumber (PK to FK o viceversa)


    SELECT * 
    from customers c
    inner join orders o
    on c.customerNumber = o.customerNumber; 
    

