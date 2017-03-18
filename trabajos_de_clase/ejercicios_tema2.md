<h2><b>Ejercicio T2.1</b></h2>
<h3><b>Calcular la disponibilidad del sistema si tenemos dos réplicas de cada elemento (en total 3 elementos en cada subsistema).</b></h3>

-> 97'75 + (1 - 97'75)*85 = 99'6625<br>
-> 97'75 + (1 - 99)*90 = 99'9<br>
-> 97'75 + (1 - 99'99)*99'9 = 99'99999<br>
-> 97'75 + (1 - 99'96)*98 = 99'9992<br>
-> 97'75 + (1 - 97'75)*85 = 99'6625<br>
-> 97'75 + (1 - 99'99)*99 = 99'9999<br>
-> 97'75 + (1 - 99'99)*99'99 = 99'99<br>
-> 97'75 + (1 - 99'75)*95 = 99'9875<br>

<b>Disponibilidad total:</b>
0,996625×0,999×0,999999×0,999992×0,996625×0,999999×0,9999×0,999875 = 99,2034961%

--------------------------------------------------

<h2><b>Ejercicio T2.2</b></h2>
<h3><b>Buscar frameworks y librerías para diferentes lenguajes que permitan hacer aplicaciones altamente disponibles con relativa facilidad.</b></h3>

<b>webControl CMS:</b><br>
El framework de desarrollo de webControl CMS está preparado para entornos de alta disponibilidad y alto rendimiento tales como servidores balanceados, clusters, granjas de servidores y entornos distribuidos. Ha sido implantado en portales con elevados volúmenes de tráfico y concurrencia, sobre distintas y muy variadas arquitecturas de red y de servidores, con excelentes resultados.




<b>PowerHA</b><br>
PowerHA SystemMirror 7.1 representa la nueva generación de soluciones de alta disponibilidad en entornos UNIX de IBM. PowerHA está basado en Cluster Aware AIX (CAA), una nueva característica de la versión 7.1 de sistema operativo líder en entornos UNIX.



<b>Hadoop</b><br>
Apache Hadoop es un framework de software que soporta aplicaciones distribuidas bajo una licencia libre. Permite a las aplicaciones trabajar con miles de nodos y petabytes de datos. Es un proyecto de alto nivel Apache que está siendo construido y usado por una comunidad global de contribuyentes,2 mediante el lenguaje de programación Java.

--------------------------------------------------

<h2><b>Ejercicio T2.3</b></h2>
<h3><b>¿Cómo analizar el nivel de carga de cada uno de los subsistemas en el servidor? Buscar herramientas y aprender a usarlas.</b></h3>

- Webserver Stress Tool. Puede ser utilizado para simular cientos o incluso miles de conexiones y ver los niveles de estrés del servidor y si los puede soportar.

- Orden "top". Útil para mostrar la carga de los procesadores y la RAM.

- JBoss ON Server Measurement Subsystem.

- Cualquier programa de monitorización como los monitores de sistema de Windows y Linux.

--------------------------------------------------

<h2><b>Ejercicio T2.4</b></h2>
<h3><b>Buscar diferentes tipos de productos: (1) Buscar ejemplos de balanceadores software y hardware (productos comerciales). (2) Buscar productos comerciales para servidores de aplicaciones. (3) Buscar productos comerciales para servidores de almacenamiento.</b></h3>

-> <b>1: Ejemplos de balanceadores software y hardware</b>

Entre los balanceadores software podemos encontrar soluciones como HAProxy que es un balanceador de cargas TCP/HTTP gratuito, LVS, Pound, UltraMonkey o Zevenet entre otros.

Como balanceadores hardware podemos destacar el LoadMaster desarrollado por las empresas KEMP y Dell, el Cisco RV082, o el TL-R488T de TP-LINK.

-> <b>2: Productos comerciales para servidores de aplicaciones.</b>

Como consecuencia del éxito del lenguaje de programación Java, el término servidor de aplicaciones usualmente hace referencia a un servidor de aplicaciones Java EE. Si nos basamos en los más populares de los últimos años, hemos de destacar a <b>Tomcat, JBoss / WildFLy, Weblogic, Jetty y GlassFish</b> principalmente.

-> <b>3: Productos comerciales para servidores de almacenamiento.</b>

Hay varias empresas que ofrecen hardware para almacenamiento comercial. Dell es una de ellas, con una amplica gama de estos dispositivos. Algunos son <b>PowerVault MD1200, Dell Storage SC9000 o Dell KACE K2000</b>.

También dispone de una amplia variedad la empresa IBM, con productos como <b>IBM FlashSystem V9000, IBM Storwize V5030F o IBM Storwize V7000F</b>.