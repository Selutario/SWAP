<h1>Práctica 6 – SWAP</h1>
Tareas realizadas:

<b>1. Realizar la configuración de dos discos en RAID 1 bajo Ubuntu, automatizando el montaje del dispositivo creado al inicio del sistema.</b><br>

Para configurarlo, simplemente hemos copiado la id que encontramos con el comando "ls -l /dev/disk/by-uuid/ y la hemos añadido al archivo fstab de manera que se arranque con cada inicio.

![uuid](https://github.com/Selutario/SWAP/blob/master/pr%C3%A1ctica%206/pantallazos/pant1.png?raw=true)
![fstab](https://github.com/Selutario/SWAP/blob/master/pr%C3%A1ctica%206/pantallazos/pant2.png?raw=true)

--------------------------------------------
<b>Simular un fallo en uno de los discos del RAID (mediante comandos con elnmdadm), retirarlo “en caliente”, comprobar que se puede acceder a la información que hay almacenada en el RAID, y por último, añadirlo al conjunto y comprobar que se reconstruye correctamente.</b><br>

![operaciones en caliente](https://github.com/Selutario/SWAP/blob/master/pr%C3%A1ctica%206/pantallazos/pant_solucion.png?raw=true)
