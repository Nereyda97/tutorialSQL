1.- Crear lista de asistencias(nombre, apellido, telefono y correo).  
2.- Agregar un campo genero.  
3.- Contar todas las mujeres de esa lista, usando el campo genero.  
4.- Contar todos los hombres de esa lista, usando el campo genero.  
5.- Encontrar los apellidos similares.  

## Markdown
El comando para convertir markdown a lo que se necesite(pdf, docx, html, etc.).  
```
$ pandoc -o [archivo de salida] [archivo de entrada]
$ pandoc -o archivo.html archivo.md
```
## DESARROLLO

El siguiente comando sirve para acceder a la base de datos.  
```{bash}
$ mysql -u nereyda -p
```
Para seleccionar la base de datos se usa el siguiente comando.  
```
mysql> use nereyda;
```

Este comando es para crear una tabla.  
```
mysql> CREATE TABLE asistencia (nombre varchar(50),apellidos varchar(50), telefono int(50), correo varchar(100));
```
Este comando muestra las tablas que se han creado.  
```
mysql> SHOW TABLES;
+-------------------+
| Tables_in_nereyda |
+-------------------+
| asistencia        |
+-------------------+
1 row in set (0.00 sec)
```
Este comando muestra lo que contiene la tabla asistencia.  
```
mysql> DESCRIBE asistencia;
+-----------+--------------+------+-----+---------+-------+
| Field     | Type         | Null | Key | Default | Extra |
+-----------+--------------+------+-----+---------+-------+
| nombre    | varchar(50)  | YES  |     | NULL    |       |
| apellidos | varchar(50)  | YES  |     | NULL    |       |
| telefono  | int(50)      | YES  |     | NULL    |       |
| correo    | varchar(100) | YES  |     | NULL    |       |
+-----------+--------------+------+-----+---------+-------+
4 rows in set (0.00 sec)
```
[Tutorial de SQL](https://www.w3schools.com/sql/sql_insert.asp)

Comado para agregar un valor a la tabla asisitencia.  
Para cada fila se repite el comando, solo cambiando la informacion de VALUES.    

```
mysql> INSERT INTO asistencia (nombre, apellidos, telefono, correo) VALUES ('Jose','Medina Talavera',5298477,'joshTal93@ejemplo.com');
```

Si se agrega correctamente aparece el siguiente dialogo.  
```
Query OK, 1 row affected (0.04 sec)
```
Modificar un campo de la tabla.  
```
mysql> ALTER TABLE [nombre tabla] CHANGE [columna_a_cambiar] [columna_cambiada] [tipo](valor) NOT NULL;
mysql> ALTER TABLE asistencia CHANGE telefono telefono VARCHAR(100) NOT NULL;
```
Si se modifica correctamente aparece el siguiente dialogo.  
```
Query OK, 0 rows affected (0.58 sec)
Records: 0  Duplicates: 0  Warnings: 0
```
Agregar una columna en la tabla se usa el siguiente comando.  
```
mysql> ALTER TABLE [nombre_tabla] ADD [nombre_columna] [tipo](valor) NOT NULL;
mysql> ALTER TABLE asistencia ADD genero VARCHAR(9) NOT NULL;
```
Si se agrega correctamente aparece el siguiente dialogo.
```
Query OK, 0 rows affected (0.54 sec)
Records: 0  Duplicates: 0  Warnings: 0
```
Para agregar desde un archivo de texto una lista hecha a comando en la terminal se siguen los siguientes pasos.  


1.- Al archivo que tiene los datos se editan para que coincidan las columnas con las columnas de la base de datos.  
2.- Una vez editados se guarda como un archivo con la extension .csv .  
3.- Se usa la siguiente paguina para convertirlo a .sql .  

[paguina para convertir a SQL](https://sqlizer.io/#/result/5XcxtAecLkPFHTfmroW7UGLJ6xzQ-qVJbQlhkxy-EeDSyzPJud0wPK931msYYfPd2opRKh8TfIAmxgpZrScVHQ==)

4.- Una vez convertido se abre con el atom, y se agregan la informacion que hace falta.  
5.- Se copea y se pega en la terminal para que se ejecute.  

Para consultar la informacion de la tabla se usa el siguiente comando.
```
SELECT nombre FROM asistencia WHERE genero="masculino";
```
