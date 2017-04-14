<h2><b>Ejercicio T4.1</b></h2>
<h3><b>Buscar información sobre cuánto costaría en la actualidad un mainframe. Comparar precio y potencia entre esa máquina y una granja web de unas prestaciones similares.</b></h3>

Recientemente, IBM sacó a la venta un mainframe (con un atractivo diseño) denominado <b>IBM zEnterprise BC12</b>. Según se informa en distintas webs, su precio rondaría los <b>75.000 dólares</b>.

Los datos que he podido encontrar son algo confusos, pero en la mayoría se habla de que es capaz de alcanzar 4900 MIPS y que soporta 489 GB de memoria RAM aproximadamente. A pesar de saber que no es una comparación muy apropiada, los procesadores Intel Xeon E7 pueden alcanzar una velocidad de compresión  de 4000 MIPS y parten con una RAM de 6 TB (hasta 24TB o más). 

Es posible que los datos sean incorrectos como ya he comentado, pero si fueran reales, con un solo Intel Xeon de 7300$ ya conseguiríamos prácticamente las mismas (o muy superiores) prestaciones web que con el mainframe de 75.000$.

--------------------------------------------------

<h2><b>Ejercicio T4.2</b></h2>
<h3><b>Buscar información sobre precio y características de balanceadores hardware específicos. Compara las prestaciones que ofrecen unos y otros.</b></h3>


<b>ZNA 6508 Hardware Appliance (ZEVENET)</b><br>
- <b>Precio:</b> 2795 euros. 
- <b>CPU:</b> Intel® CoreTM i5-6500, 3.20 GHz CON 4 cores
- <b>Memoria:</b> DDR4 2133 MHz, ECC, 4GB RAM (max. 32 GB)
- <b>Almacenamiento:</b> 16GB mSATA.
- <b>Conexiones concurrentes:</b> Soporte L2, L3, L4 y L7. No especificado.


<b>LM-3000 Server Load Balancer (KEMP)</b><br>
- <b>Precio:</b> 4875 dólares. 
- <b>CPU:</b> Intel Pentium Dual Core G850 @ 2.9GHz 
- <b>Memoria:</b> 4GB
- <b>Almacenamiento:</b> 32GB SSD
- <b>Conexiones concurrentes:</b> 8,600,000 (L4), 69,000 (L7, HTTP rquests/sec).


<b>BBF440A Barracuda Load Balancer 440 Appliance (BARRACUDA)</b><br>  
- <b>Precio:</b> 3,799.05 dólares. 
- <b>CPU:</b> No especificado.
- <b>Memoria:</b> 4GB
- <b>Almacenamiento:</b> 50-500GB disco duro.
- <b>Conexiones concurrentes:</b> Soporte L4 y L7. No especificado.

--------------------------------------------------

<h2><b>Ejercicio T4.3</b></h2>
<h3><b>Buscar información sobre los métodos de balanceo que implementan los dispositivos recogidos en el ejercicio 4.2</b></h3>

<b>ZNA 6508 Hardware Appliance:</b> 
- Por peso (weight)
- Round Robin
- Carga de CPU
- Memoria
- Menor número de conexiones (least connections)
- Menor tiempo de respuesta (least response)
- Etc (no especifica cuales más).

<b>LM-3000 Server Load Balancer</b>
- "SDN Adaptive"
- Round Robin
- Round Robin con peso (weighted Round Robin)
- Menor número de conexiones (least connections)
- Menor número de conexiones con peso (weighted least connections)
- "Agent‐based Adaptive"
- "Chained Failover (Fixed Weighting)
- IP Hash
- "Layer 7 Content Switching"
- "Global Server Load Balancing (GSLB)"
- "AD Group based traffic steering" 

<b>BBF440A Barracuda Load Balancer 440 Appliance</b>
- "Server weighting"
- "Weighted Least Connection"
- "Weighted Round Robin"
- Dice soportar múltiples esquemas de distribución pero no se especifican más.



--------------------------------------------------

<h2><b>Ejercicio T4.4</b></h2>
<h3><b> </b></h3>

Como se puede apreciar a continuación, el resultado final tras instalar la imagen en Debian del balanceador ZenLoadBalancer es muy similar al obtenido en la práctica 3. Esta máquina virtual, si estuviera configurada con unos parámetros correctos y reales de IP, dominio y servidores a los que balancear, realizaría su función perfectamente (al igual que en las prácticas con otros balanceadores como nginx o HAproxy).

![ejert4.4]()

--------------------------------------------------

<h2><b>Ejercicio T4.5</b></h2>
<h3><b>Probar las diferentes maneras de redirección HTTP. ¿Cuál es adecuada y cuál no lo es para hacer balanceo de carga global? ¿Por qué?</b></h3>

No he conseguido encontrar información al respecto de esta pregunta. En cualquier caso, esta quizá no sea la mejor solución para balanceo global ya que el hecho de tener el navegador en un idioma u en otro, podría hacer que desviaran el tráfico de un usuario a un servidor mucho más alejado del que tuviera asignado por defecto, aumentando por tanto la latencia considerablemente.

--------------------------------------------------

<h2><b>Ejercicio T4.6</b></h2>
<h3><b>Buscar información sobre los bloques de IP para los distintos países o continentes. Implementar en JavaScript o PHP la detección de la zona desde donde se conecta un usuario</b></h3>

Hay varios modos de detectar la zona de conexión del usuario. Uno de los más novedosos es mediante la utilización de API's que el uso de HTML5 permite en la actualidad. Un ejemplo en <b>Javascript</b> para la detección de la zona de conexión es el siguiente código:

    (function(){
        var content = document.getElementById("geolocation-test");

        if (navigator.geolocation)
        {
            navigator.geolocation.getCurrentPosition(function(objPosition)
            {
                var lon = objPosition.coords.longitude;
                var lat = objPosition.coords.latitude;

                content.innerHTML = "<p><strong>Latitud:</strong> " + lat + "</p><p><strong>Longitud:</strong> " + lon + "</p>";

            }, function(objPositionError)
            {
                switch (objPositionError.code)
                {
                    case objPositionError.PERMISSION_DENIED:
                        content.innerHTML = "No se ha permitido el acceso a la posición del usuario.";
                    break;
                    case objPositionError.POSITION_UNAVAILABLE:
                        content.innerHTML = "No se ha podido acceder a la información de su posición.";
                    break;
                    case objPositionError.TIMEOUT:
                        content.innerHTML = "El servicio ha tardado demasiado tiempo en responder.";
                    break;
                    default:
                        content.innerHTML = "Error desconocido.";
                }
            }, {
                maximumAge: 75000,
                timeout: 15000
            });
        }
        else
        {
            content.innerHTML = "Su navegador no soporta la API de geolocalización.";
        }
    })();

No obstante, el usuario tiene que estar utilizando un navegador que cuente con una API de geolocalización y haber dado su permiso previamente.

Fuente del código: [arumeinformatica.es](http://www.arumeinformatica.es/blog/html5-api-de-geolocalizacion-geolocation-api/)


--------------------------------------------------

<h2><b>Ejercicio T4.7</b></h2>
<h3><b>Buscar información sobre métodos y herramientas para implementar GSLB.</b></h3>

Una herramienta para implementar un balanceador de carga global podría ser NetScaler Appliances. Según su [página web](https://support.citrix.com/article/CTX110348), si quisiéramos tener un centro de datos en Estados Unidos (US), México (MX) y Colombia (CO), deberíamos seguir los siguientes pasos:

1. Si no lo hemos hecho ya, ejecutar el siguiente comando para activar la herramienta de GSLB
    > enable ns feature gslb

2. Ejecutar el siguiente comando para añadir el sitio del GSLB al dispositivo NetScaler local.
    > add gslb site site-US LOCAL 10.3.1.101

3. Ejecutar los siguientes comandos para agregar los sitios del GSLB para los dispositivos NetScaler remotos.
    > add gslb site site-MX REMOTE 172.16.1.101

    > add gslb site site-CO REMOTE 192.168.1.101

4. Ejecutar el siguiente comando para agregar los sitios del GSLB VServer que referencian al servicio utilizado en la configuración del GSLB
    > add gslb vserver gslb-lb HTTP

5. Ejecutar los siguientes comandos para agregar los servicios de GSLB para cada sitio que participa en la configuración del GSLB:
    > add gslb service gslb_SVC30 172.16.1.100 HTTP 80 -siteName site-MX

    > add gslb service gslb_SVC10 10.3.1.100 HTTP 80 -siteName site-US

    > add gslb service gslb_SVC20 192.168.1.100 HTTP 80 -siteName site-CO

6. Ejecutar los siguientes comandos para enlazar los servicios de GSLB con el GSLB VServer:
    > bind gslb vserver gslb-lb -serviceName gslb_SVC10

    > bind gslb vserver gslb-lb -serviceName gslb_SVC20

    > bind gslb vserver gslb-lb -serviceName gslb_SVC30