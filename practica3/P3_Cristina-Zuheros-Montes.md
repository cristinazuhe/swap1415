###Práctica 3. Balanceo de carga.###
Cristina Zuheros Montes

##Instalando y usando nginx.##
Lo primero que tenemos que hacer es importar la clave del repositorio tal y cómo vemos en la imagen. Posteriormente hacemos un update e instalamos nginx mediante apt-get. Al comienzo hemos visto que la conexión en nuestro balanceador es correcta.

![](https://github.com/cristinazuhe/swap1415/blob/master/practica3/imagenes/instalando1.png)

A continuación tenemos que modificar el archivo **/etc/nginx/conf.d/default.conf** de modo que quede como se nos indica en el guión. 
Ahora lanzamos nginx mediante el comando:

`servide nginx restart`

Es importante que paremos el servidor apache o directamente prescindamos de él:

![](https://github.com/cristinazuhe/swap1415/blob/master/practica3/imagenes/3nginx.png)

Probamos que todo está funcionando correctamente:

![](https://github.com/cristinazuhe/swap1415/blob/master/practica3/imagenes/probando%20curl.png)

En este caso estamos usando un método round-robin. Podemos configurar el archivo visto anteriormente para que la máquina1 tenga el doble de tabajo que la máquina 2. Simplemente tendríamos que cambiar la sección de upstream apaches del siguiente modo:

![](https://github.com/cristinazuhe/swap1415/blob/master/practica3/imagenes/pesomaquinas.png)

##Instalando y usando haproxy.##
Instalamos haproxy mediante el comando:

`apt-get install haproxy joe`

Y editamos el archivo **/etc/haproxy/haproxy.cfg** tal y como se muestra en el guión. 
Ahora lanzamos haproxy mediante:

`/usr/sbin/haproxy -f /etc/haproxy/haproxy.cfg`

Es importante que paremos nginx. Para ello usamos el comando:

`nginx -s stop`

Probamos que todo está funcionando correctamente:

![](https://github.com/cristinazuhe/swap1415/blob/master/practica3/imagenes/fin1.png)

Nota: en algunas de las imágenes vemos algunos de los errores que se pueden dar y cómo los hemos arreglado. 



