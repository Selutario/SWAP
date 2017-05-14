<h1>Práctica 4 – SWAP</h1>
Tareas realizadas:

<b>1. Instalar un certificado SSL autofirmado para configurar el acceso HTTPS a los servidores.</b><br>

![certificado autofirmado]()

Como se puede ver en la imagen, una vez que hemos rellenado los datos que requiere el programa que crea un certificado autofirmado, indicamos dentro del archivo de configuración de Apache /etc/apache2/sites-available/default-ssl la ruta de los certificados.

Tras ello, al realizar una llamada desde la Máquina 2 a la ruta de la máquina 1 (curl -k https://192.168.1.100), nos responde sin problemas.

En la siguiente imagen se pueden apreciar ambas máquinas respondiendo a llamadas desde el puerto 443:

![ssl en M1 y M2]()

--------------------------------------------
<b>2. Configurar las reglas del cortafuegos con IPTABLES para asegurar el acceso a los servidores web, permitiendo el acceso por los puertos de HTTP y HTTPS. Esta configuración se puede hacer en la misma máquina balanceadora. En cualquier caso se debe poner en un script que se ejecute en el arranque del sistema.</b><br>

En mi caso he optado por configurar las reglas de manera individual en cada máquina, en vez de hacerlo en el balanceador, aunque el resultado es más sencillo de gestionar a la larga si se hace en dicho balanceador. 

He seguido la configuración aconsejada en el guión de prácticas para un servidor web, creando el siguiente script (idéntico en la máquina 1 y la máquina 2):

![Script iptables]()

Por último, para que estas reglas se guarden de manera permanente, manteniéndose tras cada reinicio, he guardado las reglas actuales con iptables-save y he escrito una línea dentro del archivo de redes /etc/network/interfaces que permita cargar esa configuración cada vez que ese archivo es cargado:

    iptables-save > /etc/network/iptables.rules
    sudo nano /etc/network/interfaces

        iface enp0s8 inet static
            ...
        pre-up iptables-restore < /etc/network/iptables.rules



--------------------------------------------
<b>3A. [OPCIONAL] Realizar instalación de certificado del proyecto Certbot</b><br>

Estuve intentando realizar un proxy inverso (reverse proxy) con conexión por SSL en un servidor de descargas que ya tenía instalado en una raspberry pi, el cual cuenta con dominio que siempre apunta a la ip pública actual de la red en la que se encuentra la raspberry de modo que me permite añadir nuevos torrents remotamente.

No obstante, dicho servidor se encuentra instalado sobre una imagen en Debian jessie, para la cual no hay por el momento versiones de <b>nginx</b> más actuales que la v1.6.5, requiriendo como mínimo una 1.9.5 para las conexiones por HTTPS. 

Por ello, a pesar de haberlo configurado todo y tener los certificados de Let's Encrypt correctos, fallé al poner en marcha el servicio de nginx puesto que había varias líneas del archivo de configuración que no reconocía por tratarse de una versión inferior. 

No obstante, dejo aquí una imagen que muestra como era el proceso de creación de un certificado Certbot/Let's Encrypt mediante SSH (se muestra cortada para no mostrar al completo la clave generada):

![SSL Raspberry pi]()

--------------------------------------------

<b>3B. [OPCIONAL] Configurar cortafuegos en una máquina intermedia distinta al balanceador</b><br>

Siguiendo el PDF que Pedro creó sobre como realizar esta parte opcional, he creado el script del cortafuegos que, a parte de realizar sus tareas habituales de filtrado de paquetes, redirecciona estos a la máquina indicada, de modo que podría situarse en un punto de la red en que protega los servidores pero libere al balanceador de la tarea de filtrado.

En esta primera imagen vemos el script resultante:

![Script filtrado]()


Y en esta otra, vemos el comportamiento al llamar a la máquina filtradora (firewall) antes y después de aplicar el script:

![Script filtrado 2]()