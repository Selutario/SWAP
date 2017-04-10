<h1>Práctica 3 – SWAP</h1>
Tareas realizadas:

<b>1. configurar una máquina e instalarle el nginx como balanceador de carga</b><br>

[nginx balanceado](https://raw.githubusercontent.com/Selutario/SWAP/master/pr%C3%A1ctica%203/pantallazos/NGINX-balanceado.png)

En la imagen superior se puede apreciar como, con <b>nginx</b> corriendo como balanceador en la máquina 3, las llamadas que recibe las reparte entre la máquina 1 y la máquina 2 mediante el algoritmo de round-robin.

--------------------------------------------
<b>2. configurar una máquina e instalarle el haproxy como balanceador de carga</b><br>

[haproxy balanceado](https://raw.githubusercontent.com/Selutario/SWAP/master/pr%C3%A1ctica%203/pantallazos/haproxy-balanceado.png)

Aquí nos encontramos con un resultado idéntido puesto que estamos usando también el algoritmo round-robin. La diferencia radica en que esta vez, quien hace las veces de balanceador es <b>haproxy</b>. La diferencia podremos apreciarla en el rendimiento posteriormente.

La configuración realizada para su correcto funcionamiento ha sido la siguiente:
[configuración haproxy](https://raw.githubusercontent.com/Selutario/SWAP/master/pr%C3%A1ctica%203/pantallazos/haproxyCONF.png)

--------------------------------------------
<b>3. [OPCIONAL] configurar una máquina e instalarle el pound como balanceador de carga</b><br>

[pound balanceado](https://raw.githubusercontent.com/Selutario/SWAP/master/pr%C3%A1ctica%203/pantallazos/pound-balanceado.png)

En este caso apreciamos que el balanceo en <b>pound</b> no utiliza el mismo algoritmo, pues a veces desvía más conexiones a una máquina que a otra. Para configurarla, he dejado los valores de usuario, grupo y control por defecto. El resto puede verse aquí: [configuración pound](https://raw.githubusercontent.com/Selutario/SWAP/master/pr%C3%A1ctica%203/pantallazos/conf-pound.png)

--------------------------------------------
<b>4. 3. someter a la granja web a una alta carga, teniendo primero nginx y después haproxy.</b><br>

Se ha utilizado la siguiente orden con los 3 tipos de balanceadores:

    ab -n 20000 -c 10 http://192.168.1.102/index.html

- Resultados de someter NGINX a una carga de 20.000 conexiones: 6.823 segundos
- Resultados de someter HAPROXY a una carga de 20.000 conexiones: 7.263 segundos
- Resultados de someter POUND a una carga de 20.000 conexiones: 15.009 segundos

Para más detalles sobre los benchmarks:
[Benchmark NGINX](https://raw.githubusercontent.com/Selutario/SWAP/master/pr%C3%A1ctica%203/pantallazos/nginx_20000bm.png) | 
[Benchmark HAPROXY](https://raw.githubusercontent.com/Selutario/SWAP/master/pr%C3%A1ctica%203/pantallazos/haproxy-20000bm.png) | 
[Benchmark POUND](https://raw.githubusercontent.com/Selutario/SWAP/master/pr%C3%A1ctica%203/pantallazos/pound-20000bm.png)