###Práctica 4. Comprobar el rendimiento de servidores web.###
Cristina Zuheros Montes

##Usando Apache Bechmarck.##
Comprobamos el rendimiento de una sóla máquina servidora y de la granja web. Para ello vamos a realizar 100000 peticiones concurrentemente de 100 en 100 mediante el comando:

`ab -n 100000 -c 100 http://ip_maquina/prueba.html`

Veamos los resultados:

media_s es la media en una sóla máquina servidora.

media_n es la media en la granja web con el balanceador nginx.

media_h es la media en la granja web con el balanceador haproxy.

Uso una notación análoga para las desviaciones.

![](https://github.com/cristinazuhe/swap1415/blob/master/practica4/imagenes/imagen1ab.png)

![](https://github.com/cristinazuhe/swap1415/blob/master/practica4/imagenes/ab1.png)

![](https://github.com/cristinazuhe/swap1415/blob/master/practica4/imagenes/ab2.png)

![](https://github.com/cristinazuhe/swap1415/blob/master/practica4/imagenes/ab3.png)


##Usando httperf.##
En este caso abriremos un total de 27000 conexiones TCP y las haremos a 500 peticiones por segundo. Veamos el comando:

`httperf --server ip_maquina --port 80 --uri /prueba.html --rate 500 --num-conn 27000 --num-call l --timeout 5`

Veamos los resultados:

![](https://github.com/cristinazuhe/swap1415/blob/master/practica4/imagenes/imagen1httperf.png)

![](https://github.com/cristinazuhe/swap1415/blob/master/practica4/imagenes/htt1.png)

![](https://github.com/cristinazuhe/swap1415/blob/master/practica4/imagenes/htt2.png)

![](https://github.com/cristinazuhe/swap1415/blob/master/practica4/imagenes/htt3.png)

![](https://github.com/cristinazuhe/swap1415/blob/master/practica4/imagenes/htt4.png)


##Usando OpenWebLoad.##
Pondremos como número de clientes simultáneos 1000:

`openload http://ip_maquina 1000`

![](https://github.com/cristinazuhe/swap1415/blob/master/practica4/imagenes/imagen1open.png)

![](https://github.com/cristinazuhe/swap1415/blob/master/practica4/imagenes/open1.png)

![](https://github.com/cristinazuhe/swap1415/blob/master/practica4/imagenes/open2.png)



