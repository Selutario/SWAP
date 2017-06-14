<h1>Práctica 5 – SWAP</h1>
Tareas realizadas:

<b>1. Crear una BD con al menos una tabla y algunos datos</b><br>

![Tabla creada](https://github.com/Selutario/SWAP/blob/master/pr%C3%A1ctica%205/pantallazos/pant1_bd_creada.png?raw=true)

--------------------------------------------
<b>2. Realizar la copia de seguridad de la BD completa usando mysqldump.</b><br>

Como se puede apreciar en la siguiente imagen, he importado en la máquina 2 una copia realizada mediante <b>mysqldump</b> a través de scp.

Copia importada: 
![Importada](https://github.com/Selutario/SWAP/blob/master/pr%C3%A1ctica%205/pantallazos/pant1_scp.png?raw=true)


--------------------------------------------
<b>3. Restaurar dicha copia en la segunda máquina (clonado manual de la BD).</b><br>

Aplicamos la copia a la base de datos en la segunda máquina:
![Restaurar copia](https://github.com/Selutario/SWAP/blob/master/pr%C3%A1ctica%205/pantallazos/pant2_copia_aplicada.png?raw=true)


--------------------------------------------

<b>Realizar la configuración maestro-esclavo de los servidores MySQL para que la replicación de datos se realice automáticamente</b><br>

A continuación se puede apreciar cómo en la base de datos 1 se inserta una nueva fila, que aparece de manera instantánea en la 2
![Maestro-esclavo](https://github.com/Selutario/SWAP/blob/master/pr%C3%A1ctica%205/pantallazos/pant5_automatico.png?raw=true)