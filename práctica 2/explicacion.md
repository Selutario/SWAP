<h1>Práctica 2 – SWAP</h1>
Tareas realizadas:

<u>1. probar el funcionamiento de la copia de archivos por ssh</u><br>

[Paso1](https://raw.githubusercontent.com/Selutario/SWAP/master/pr%C3%A1ctica%202/pantallazos/Paso1.png)

Aquí se puede comprobar como tras ejecutar el comando rsync, la máquina 2 se trae el archivo existe únicamente en la máquina 1 hasta ese momento (prueba.html).

--------------------------------------------
<u>2. clonado de una carpeta entre las dos máquinas</u><br>

[Paso2](https://raw.githubusercontent.com/Selutario/SWAP/master/pr%C3%A1ctica%202/pantallazos/Paso2.png)

En las fotos se aprecia como, al igual que los archivos de texto, las carpetas aparecen en la máquina 2 tras ejecutar rsync.

--------------------------------------------
<u>3. configuración de ssh para acceder sin que solicite contraseña</u><br>

[Paso3](https://raw.githubusercontent.com/Selutario/SWAP/master/pr%C3%A1ctica%202/pantallazos/Paso3.png)

Tras haber copiado la clave pública en la máquina 1 (M1), se puede acceder como normalmente pero con la diferencia de que no es necesario introducir la contraseña.

--------------------------------------------
<u>4. establecer una tarea en cron que se ejecute cada hora para mantener actualizado el contenido del directorio /var/www entre las dos máquinas</u><br>

[Paso4](https://raw.githubusercontent.com/Selutario/SWAP/master/pr%C3%A1ctica%202/pantallazos/Paso4.png)

Se puede apreciar como, tras el tiempo establecido en la tabla crontab, se ejecuta el comando rsync de manera automática, copiando todo los cambios producidos desde la última actualización.