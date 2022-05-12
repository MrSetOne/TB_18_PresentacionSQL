# TB_18_PresentacionSQL

## Introducción
MySQL es un sistema de gestión de bases de datos relacionales considerado como la base de datos de código abierto más popular del mundo, especialmente para los entornos de desarrollo web que nos interesan.

¿Cuáles son los principales objetivos de este proyecto?
⦁ Entender que es una base de datos relacional
⦁ Comprender cómo se realizan las consultas a una base de datos
⦁ Entender cómo interactuar con los datos almacenados en la base de datos.

## 1.1 Crea una base de datos

A continuación, crearás una base de datos. El objetivo de este proyecto es aprender a trabajar en una base de datos y hacer consultas SQL.

### 1.1.1 Crea una base de datos

Crea una base de datos que se llame my_company_database. La base de datos deberá contener la siguiente tabla:

* employees. A su vez tendrá los siguientes campos:   
    * id
    * birth_date  
    * first_name
    * last_name   
    * gender

```SQL
CREATE TABLE employees (id INT AUTO_INCREMENT, birth_date DATE, first_name VARCHAR(20), last_name VARCHAR(20), gender VARCHAR(20), PRIMARY KEY(id));
```

### 1.1.2 Añade columnas nuevas a la tabla creada
Añade 3 columnas nuevas a la tabla:
Columna "salary"
Columna "title"
Columna "title_data"

```SQL
ALTER TABLE employees ADD salary FLOAT;
ALTER TABLE employees ADD title VARCHAR(20);
ALTER TABLE employees ADD title_date DATE;
```

## 1.2. Ejecute las siguientes consultas SQL

A continuación, deberá realizar las siguientes consultas SQL:

### 1.2.1 INSERTAR DATOS

* Inserte al menos 15 nuevos empleados:
    * Al menos 3 empleados deben tener el mismo nombre.
    * Los salarios de los empleados deben oscilar en un rango de
    * 5000 y 50.000 y deben variar entre diferentes géneros.
    * Todos los empleados tienen un título.
    * Al menos 5 títulos son de 2020.

```SQL
INSERT INTO employees (birth_date, first_name, last_name, gender, salary, title, title_date)
values ('1994-01-18', 'Michael', 'Lara', 'tomate', 50000,'FullStack',2022),
('1990-04-18', 'Julian', 'Smith', 'aguacate', 20000,'Liador de porros',2022),
('1992-05-12', 'Michael', 'La Polla', 'pato', 10000,'Paluquero de calvos',2020),
('1394-01-18', 'Paco', 'Lara', 'tomate', 30000,'Liador de porros',2020),
('1994-01-18', 'Michael', 'Lara', 'tomate', 5000,'Profesor',2011),
('1694-01-18', 'Julian', 'Del Huerto', 'rucula', 50000,'Paluquero de calvos',2020),
('1994-01-18', 'Ruben', 'Lara', 'pera', 5000,'El tio que hace eso',2020),
('1994-01-18', 'Rebeca', 'La Polla', 'pato', 50000,'Paluquero de calvos',2011),
('994-01-18', 'Elena', 'Nito del Bosque', 'tomate', 50000,'Liador de porros',2020),
('1994-01-18', 'Lupicinio', 'Del Huerto', 'pera', 50000,'FullStack',2011),
('1974-01-18', 'Aitor', 'Tilla', 'pato', 50000,'Paluquero de calvos',2011),
('1994-01-18', 'Uctumbu', 'Malucmu', 'pera', 5000,'Liador de porros',1901),
('1794-01-18', 'Lupicinio', 'Del Huerto', 'rucula', 10000,'El tio que hace eso',1901),
('194-01-18', 'Paco', 'Lara', 'pato', 50000,'Liador de porros',2020),
('1996-01-18', 'Rosa', 'Melano', 'tomate', 35000,'FullStack',1901);
```

### 1.2.2 ACTUALIZAR DATOS

* Actualizar a los empleados:

    * Cambiar el nombre de un empleado. Para ello, genere una consulta que afecte solo a un determinado empleado en función de su nombre, apellido y fecha de nacimiento.

```SQL
UPDATE employees SET first_name = 'Sofia' WHERE id = 67;
```

### 1.2.3 OBTENER DATOS

* Seleccione todos los empleados con un salario superior a 20.000
```SQL
SELECT salary, CONCAT(first_name, ' ', last_name) AS 'Name' FROM employees WHERE salary > 20000;
```

* Seleccione todos los empleados con un salario inferior a 10,000
```SQL
SELECT salary, CONCAT(first_name, ' ', last_name) AS 'Name' FROM employees WHERE salary < 20000;
```

* Seleccione todos los empleados que tengan un salario entre 14,000 y 50.000
```SQL
SELECT salary, CONCAT(first_name, ' ', last_name) AS 'Name' FROM employees WHERE salary > 14000 AND salary < 50000;
```

* Seleccione el número total de empleados
```SQL
SELECT COUNT(id) FROM employees;
```

* Selecciona los títulos del año 2019
```SQL
SELECT title_date, CONCAT(first_name, ' ', last_name) AS 'Name' FROM employees WHERE title_date = 2019;
```

* Seleccione solo el nombre de los empleados en mayúsculas
```SQL
SELECT UCASE(first_name) FROM employees;
```

* Seleccionar el nombre de los empleados sin que se repita ninguno
```SQL
SELECT DISTINCT first_name FROM employees;
```

### 1.2.4 BORRAR DATOS

* Elimina el empleado con id = 5
```SQL
DELETE FROM employees WHERE id = 5;
```

* Eliminar a todos los empleados con un salario superior a 20.000
```SQL
DELETE FROM employees WHERE salary > 20000;
```