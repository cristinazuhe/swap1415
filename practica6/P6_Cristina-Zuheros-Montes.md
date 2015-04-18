###Práctica 6. Discos en RAID.###
Cristina Zuheros Montes

##Configuación del RAID.##
Hemos optado por crear una nueva máquina virtual UbuntuServer para trabajar con el RAID. En primer lugar creamos la máquina virtual y añadimos un segundo disco duro con la misma configuración que el que se nos crea por defecto. Procedemos a realizar la instalación como de costumbre. 
A la hora de realizar el particionado de discos, indicaremos que lo vamos a hacer manualmente:

Seleccionamos el primer disco y creamos una nueva tabla de particiones. Sobre el espacio libre que se nos muestra, creamos una partición nueva a la que le daremos un tamaño de, por ejemplo, 1GB. Será una partición primaria y estará al principio del disco. En cuanto a cómo utilizarla, le indicaremos que se use como área de intercambio. Finalizamos y veremos que ya se ha creado en nuestro primer disco.
Ahora nos vamos al espacio libre que queda en ese mismo disco y creamos una nueva partición sobre él, también primaria, pero le daremos mayor tamaño, por ejemplo, de 20.5GB. Esta vez la utilizaremos como volumen físico para RAID. Finalizamos la partición.

Seleccionamos el segundo disco y lo configuramos tal y como hemos configurado el primero. 

Tras la configuración de ambos discos, guardaremos los cambios gracias a la opción configurar RAID por sofware.

Ahora tendremos que crear un dispositivo MD, que será de tipo RAID1. El número de dispositivos activos para el RAID1 será 2, y el de dispositivos libres 0.

Ahora elegimos las 2 particiones que formarán el RAID1 (como vemos en la imagen) y terminamos:

![](https://github.com/cristinazuhe/swap1415/blob/master/practica6/imagenes/3.png)

Volvemos a nuestra ventana principal de particionado de discos y ya tenemos el RAID1. Vamos a asignarle un sistema de ficheros (ext4) y un punto de montaje(/) y terminamos la partición.  

Finalizamos la instalación como de costumbre y probamos que todo es correcto usando el comando

`sudo mdadm --detail /dev/md0`

![](https://github.com/cristinazuhe/swap1415/blob/master/practica6/imagenes/2.png)