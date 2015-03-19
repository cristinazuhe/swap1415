## Práctica 2. Clonar la información de un sitio web##
Cristina Zuheros Montes

### Usando rsync. ###
Instalamos la herramienta rsync mediante la orden: 
`sudo apt-get install rsync`

y se nos muestra que, en verdad, ya lo tenemos instalado en nuestras máquinas (se verá en la siguiente imagen). 

Vamos a clonar una los archivos que tenemos en /var/www/ para ver que realmente funciona: 

![](https://github.com/cristinazuhe/swap1415/blob/master/practica2/imagenes/rsync1.png)

###Acceso sin contraseña para ssh.###
Generamos la clave mediante ssh-keygen tal y como vemos en la captura:

![](https://github.com/cristinazuhe/swap1415/blob/master/practica2/imagenes/contrase%C3%B1a1.png)

Podemos copiar la clave mediante:
`ssh-copy-id -i .ssh/id_dsa.pub root@192.168.1.100.`

Veamos que nos podemos conectar desde nuestra máquina2 a nuestra máquina1:

![](https://github.com/cristinazuhe/swap1415/blob/master/practica2/imagenes/contrase%C3%B1a2.png)

###Usando crontab.###
Vamos a crear una tarea en cron que se ejecute cada hora para mantener actualizado el contenido del directorio /var/www/ entre las dos máquinas. Para ello, tenemos que editar el archivo **/etc/crontab** y hacer uso de la orden que hemos visto anteriormente:

![](https://github.com/cristinazuhe/swap1415/blob/master/practica2/imagenes/fin1.png)