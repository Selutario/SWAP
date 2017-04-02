<h2><b>Ejercicio T3.1</b></h2>
<h3><b>Buscar con qué órdenes de terminal o herramientas gráficas podemos configurar bajo Windows y bajo Linux el enrutamiento del tráfico de un servidor para pasar el tráfico desde una subred a otra.</b></h3>

<b> Bajo linux: </b>

Para activar el enrutamiento en un sistema Linux, tan solo basta con poner a '1' la variable ip_forward del sistema:

    // Activar el enrutamiento en un sistema Linux
    sudo echo "1" > /proc/sys/net/ipv4/ip_forward

Tendríamos que indicar que se acepten todos los paquetes que son para reenviar, es decir, aquellos que llegan a nuestra máquina pero que no es ella la destinataria (lo cual conseguimos al aceptar los paquetes de tipo FORWARD).

También habría que indicar que los paquetes que lleguen desde la red interna (por ejemplo 10.0.0.0/8) y que salgan hacia el router (desde eth0) después de ser enrutados en nuestra máquina, han de ser enmascarados.

    // Haciendo NAT en el servidor
    sudo iptables -A FORWARD -j ACCEPT
    sudo iptables -t nat -A POSTROUTING -s 10.0.0.0/8 -o eth0 -j MASQUERADE

De este modo estaríamos convirtiendo nuestra máquina/servidor en un router, por el que pasa el tráfico desde una subred a otra o a internet.

<br>
<b> Bajo Windows: </b>

- Iremos a inicio> Administrador del servidor> Funciones> Agregar funciones

- En la pantalla de funciones del servidor seleccionaremos la casilla de servicios de acceso y directivas de redes

- En la servicios de función activamos la de servicio de enrutamiento y acceso remoto, con lo que lo harán sus dos casillas hijas

- Nos aparece la ventana resumen, procedemos a instalar

- Cuando termine y esté todo correcto cerramos

- Para configurarlo iremos a inicio >Herramientas administrativas> Enrutamiento y acceso remoto

- Una vez instalado debemos habilitar el servicio, haciendo click derecho sobre el nombre del servidor, configurar y habilitar Enrutamiento y acceso remoto

- Aparecerá un asistente en el que debemos seleccionar Traducción de direcciones de red (NAT)

- En la siguiente ventana seleccionamos la tarjeta conectada a Internet, siguiente
     
-  Ahora seleccionamos una de las ipś de nuestro servidor por la que los clientes accederan a Internet, después se podrán agregar las demás

- El asistente finaliza, ya tenemos la flechita verde indicando que todo está correcto


Para añadir las otras interfaces:

- Vamos a ipv4> click derecho sobre General> Interfaz nueva…

- Elegimos las tarjetas que falten de las disponibles, aceptamos

- La siguiente ventana la aceptamos sin modificar nada

- Click derecho sobre el nombre del servidor, todas las tareas> Reiniciar

----------------------
<h2><b>Ejercicio T3.2</b></h2>
<h3><b>Buscar con qué órdenes de terminal o herramientas gráficas podemos configurar bajo Windows y bajo Linux el filtrado y bloqueo de paquetes.</b></h3>

<b> En linux: </b>

La herramienta más sencilla para realizar el filtrado de paquetes en linux es iptables. Algunos ejemplos de reglas son:

    // No deja la salida a ningún lugar
    iptables -A OUTPUT -j DROP

    // Borra todas las reglas
    iptables -F

    // Listar las reglas que hay
    iptables -L      

    // Prohibir la salida por el puerto 80     
    iptables -A OUTPUT -p tcp --destination-port 80 -j DROP

    // Prohibir la navegación hacía una página
    iptables -A OUTPUT -d 178.33.118.246 -j DROP

    // Evitar que una IP nos envíe datos
    iptables -A INPUT -s 192.168.66.1 -j DROP


<b> En Windows: </b>

En windows se puede utilizar como herramienta de filtrado el propio servicio de firewall que ya viene instalado por defecto.


------------------------
<h3>Bibliografía:</h3>

[www.ite.educacion.es](http://www.ite.educacion.es/formacion/materiales/85/cd/linux/m6/enrutamiento_en_linux.html)

[jucarmona.wordpress.com](https://jucarmona.wordpress.com/2013/03/12/servicio-de-acceso-remoto-y-enrutamiento-para-servidor-dhcp-en-windows-2008-server/)

[www.solvetic.com](https://www.solvetic.com/tutoriales/article/2889-como-utilizar-iptables-para-filtrar-paquetes-linux/)