<h2><b>Ejercicio T5.1</b></h2>
<h3><b>Buscar información sobre cómo calcular el número de conexiones por segundo. </b></h3>

Hay varios comandos que pueden permitirnos conocer éste dato. Un ejemplo sería con el comando netstat:

    netstat | grep http | wc -l

Aunque también podríamos hacerlo consultando los log de acceso en Apache por ejemplo

    tail -f /var/log/apache2/access.log

O haciendo uso de herramientas gráficas como [Webmin](http://www.webmin.com/)

--------------------------------------------------

<h2><b>Ejercicio T5.2</b></h2>
<h3><b>Instalar wireshark y observar cómo fluye el tráfico de red en uno de los servidores web mientras se le hacen peticiones HTTP.</b></h3>

Como los servidores web que hemos configurado en las prácticas son Ubuntu server y por tanto no disponen de un entorno gráfico donde ejecutar la interfaz de Wireshark, he hecho uso de un comando para ejecutarlo en la terminal. Es parte del mismo proyecto de wireshark:

    sudo tshark -f 'tcp port 80 and http'

No obstante, se produce un error que no he llegado a solucionar pero que muestro a continuación:

![wireshark]()

--------------------------------------------------

<h2><b>Ejercicio T5.3</b></h2>
<h3><b>Buscar información sobre características, disponibilidad para diversos SO, etc de herramientas para monitorizar las prestaciones de un servidor.</b></h3>

<b><u># top</u></b>: Muestra el uso de CPU, uso de memoria, la memoria de intercambio, caché, tamaño de búfer, PID de proceso, usuario, etc. 

<b><u># vmstat</u></b>: Muestra las estadísticas de la memoria virtual, hilos kernerl, discos, procesos de sistema, bloques de E / S, interrupciones, actividad de la CPU.

<b><u># netstat -a | more</u></b>: Sirve para monitorear el desempeño de la red y solucionar problemas relacionados con la red. 

<b><u># lsof</u></b>: Se utiliza para mostrar todos los archivos abiertos y los procesos que los utilizan. Los archivos abiertos incluidos son archivos de disco, de la red, tuberías, dispositivos y procesos.

<b><u># tcpdump -i eth0</u></b>: Se utiliza tanto para la captura o el filtro de paquetes TCP/IP que recibieron o han sido transferidos en una interfaz específica a través de una red. También proporciona una opción para guardar los paquetes capturados en un archivo para su posterior análisis. 

<b><u># iotop</u></b>: Es muy similar a al comando top y al programa htop, pero tiene la función de contabilidad para monitorear y visualizar en tiempo real las E/S del disco y procesos.

<b><u># IPTraf</u></b>: Recoge una gran variedad de información como monitor de tráfico IP que pasa a través de la red, incluida la información de flags TCP, detalles ICMP, TCP / averías tráfico UDP, paquete de conexión TCP y cuenta Byne.

--------------------------------------------------