###Práctica 3. Balanceo de carga.###
Cristina Zuheros Montes

##Instalando y usando nginx.##
Lo primero que tenemos que hacer es importar la clave del repositorio tal y cómo vemos en la imagen. Posteriormente modificamos el fichero /etc/apt/sources.list añadiendo las líneas que vemos en la imagen 2, hacemos update e instalamos nginx mediante apt-get.

![](https://github.com/cristinazuhe/swap1415/blob/master/practica3/imagenes/vmware/1.png)

![](https://github.com/cristinazuhe/swap1415/blob/master/practica3/imagenes/vmware/2.png)

A continuación tenemos que modificar el archivo **/etc/nginx/conf.d/default.conf** de modo que quede como se nos indica en el guión. 
Ahora lanzamos nginx (es importante que paremos el servidor apache o directamente prescindamos de él) mediante el comando:

`servide nginx restart`

![](https://github.com/cristinazuhe/swap1415/blob/master/practica3/imagenes/vmware/3.png)

Probamos que todo está funcionando correctamente:
![](https://github.com/cristinazuhe/swap1415/blob/master/practica3/imagenes/vmware/5.png)

![](https://github.com/cristinazuhe/swap1415/blob/master/practica3/imagenes/vmware/5.png)

En este caso estamos usando un método round-robin. Podemos configurar el archivo visto anteriormente para que la máquina1 tenga el doble de tabajo que la máquina 2. Simplemente tendríamos que cambiar la sección de upstream apaches del siguiente modo:

![](https://github.com/cristinazuhe/swap1415/blob/master/practica3/imagenes/vmware/4.png)

##Instalando y usando haproxy.##
Instalamos haproxy mediante el comando:

`apt-get install haproxy joe`

Y editamos el archivo **/etc/haproxy/haproxy.cfg** tal y como se muestra en el guión. 
Ahora lanzamos haproxy mediante:

`/usr/sbin/haproxy -f /etc/haproxy/haproxy.cfg`

Es importante que paremos nginx. Para ello usamos el comando:

`nginx -s stop`

![](https://github.com/cristinazuhe/swap1415/blob/master/practica3/imagenes/vmware/7.png)

Probamos que todo está funcionando correctamente:

![](https://github.com/cristinazuhe/swap1415/blob/master/practica3/imagenes/vmware/8.png)






