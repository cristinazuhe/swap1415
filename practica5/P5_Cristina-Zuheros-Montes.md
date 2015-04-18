###Práctica 5. Replicación de bases de datos MySQL.###
Cristina Zuheros Montes

##Creando la BD en MySQL.##
En primer lugar vamos a crear una base de datos e insertaremos algunos datos en ella.
Entramos en MySQL y ejecutamos los siguientes comandos:

`create database contactos;`

`use contactos;`

`create table datos(nombre varchar(100),tlf int);`

`insert into datos(nombre,tlf) values ("pepe", 958132123);`

y podemos ver que ya lo tenemos creado:

![](https://github.com/cristinazuhe/swap1415/blob/master/practica5/imagenes/2.png)

##MySQLDump. Replicando la BD.##
Antes de hacer la copia de seguridad vamos a evitar poder hacer cambios en la BD. Para ello volvemos a entrar en MySQL, en nuestra máquina principal donde hemos creado la base de datos, y ejecutamos:
`FLUSH TABLES WITH READ LOCK;`

 Hacemos mysqldump en la máquina principal y desbloqueamos las tablas (ver imagen). Ahora sólo falta ir a la máquina secundaria y copiar el archivo .SQL (ver imagen).

![](https://github.com/cristinazuhe/swap1415/blob/master/practica5/imagenes/3.png)

Ahora tendremos que importar la BD completa en la máquina secundaria. Para ello accedemos a MySQL, creamos la BD y restauramos los datos.

![](https://github.com/cristinazuhe/swap1415/blob/master/practica5/imagenes/4.png)

Veamos que ya sí tenemos la BD replicada:

![](https://github.com/cristinazuhe/swap1415/blob/master/practica5/imagenes/5.png)

##Replicación de BD mediante maestro-esclavo.##
Tanto en el maestro como en el esclavo, modificamos el archivo **/etc/mysql/my.cnf** como se nos indica en el guión y reiniciamos el servicio mediante:
`/etc/init.d/mysql restart`

![](https://github.com/cristinazuhe/swap1415/blob/master/practica5/imagenes/6-reiniciamoselservicio.png)

Ahora nos vamos al esclavo y creamos un usuario al cual le damos permisos de acceso:
`CREATE USER esclavo IDENTIFIES BY 'esclavo';`
`GRANT REPLICATION SLAVE ON *.* TO 'ESCLAVO'@'%'IDENTIFIED BY 'esclavo';`
`FLUSH PRIVILEGES;`
`FLUSH TABLES;`
`FLUSH TABLES WITH READ LOCK;`

En el maestro obtenemos el master_log_file y master_log_pos mediante el comando que se muestra en la imagen (a la izquierda) para poder darle los datos al esclavo:
`CHANGE MASTER TO MASTER_HOST='192.168.243.128'`
`MASTER_USER='esclavo', MASTER_PASSWORD='esclavo'`
`MASTER_LOG_FILE='bin.000003',MASTER_LOG_POS=1329,`
`MASTER_POST=3306;`

Arrancamos el esclavo y desbloqueamos las tablas. Vemos que todo está correcto (ver imagen a la derecha) mediante:
`SHOW SLAVE STATUS\G`

![](https://github.com/cristinazuhe/swap1415/blob/master/practica5/imagenes/7.png)

Finalmente vemos que si añadimos datos en la BD del maestro, se replica en la del esclavo:

![](https://github.com/cristinazuhe/swap1415/blob/master/practica5/imagenes/8-PROBANDOQUEFUNCIONA.png)




