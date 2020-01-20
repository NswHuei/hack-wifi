# hack-wifi WEP
Vamos a probar romper la contraseña de un red wifi con "[Kali](https://www.kali.org/downloads/)" usando la herramienta "aircrack"
Para este práctica necesitamos **adaptador inalámbrico** en tu PC. 
Con cualquier herramienta para crear usb de arranque (ej: [rufus](https://rufus.ie/)) creamos un usb de arranque con el iso de kali. Cuando termines encedemos tu pc con el usb de arranque.

Arrancamos el equipo desde live USB y entramos al sistema en live system. Si tienes ya instalada el Kali entras directamente. En el caso que interesa hacer esta práctica en máquinas virtuales necesita un adaptadow wifi de USB para poder hacer la práctica correctamente.

![refresca la página para cargar el imágen](imagen/kali1.png)

Abrimos el terminal e introducimos el comando:
>airmon-ng

Nos aparecerá el interfaz wlan con el controladore del red wifi que tenemos instalado y reconocido por la herramienta. Si no te aparece nada pueden ser que tu controlador no soporta la función de monitorizar el red wifi.

![refresca la página para cargar el imágen](imagen/kali2.png)

Una vez comprobado que la herramienta es compatible con nuestro controlador empezamos a monitoriza el interfaz wlan0. 
>airmon-ng start wlan0

Nos indica el comando que el proceso **1044** **1107** pueden causar problemas, lo apagamos con el comando ```kill```.
>kill -9 1044

Una vez iniciado el interfaz **wlan0** se convierte en **wlan0mon**, podemos comprobarlo con ```ifconfig```.

![refresca la página para cargar el imágen](imagen/kali3.png)

Escaneamos el red wifi con el comando:
>airodump-ng wlan0mon

Nos mostrará el BSSID(mac) de los routers o PA, intensidad de señal, modo de cifrado y el nombre del dispositivo(ESSID). Una vez encontrado el red que queremos atacar terminamos el escaneo con ```ctrl+c```

![refresca la página para cargar el imágen](imagen/kali4.png)

Usamos el comando ```airodump-ng``` para coger los paquetes del red "víctima".
>airodump-ng -c 6 --bssid E8:DE:27:2F:84:CA -w ./ wlan0mon

```-c```El canal del wifi.

```--bssid```La mac del router.

```-w```El lugar donde vamos a guardar los paquetes capturado.
Una vez teniendo suficiente paquetes podemos empezar a "hackear" la contraseña.

Con el comando ```aireplay-ng``` aceleramos el paso de capturar paquetes. Para más información consulta al [Aireplay](https://www.aircrack-ng.org/doku.php?id=es:aireplay-ng).

![refresca la página para cargar el imágen](imagen/kali5.png)

>aireplay-ng -3 -b E8:DE:27:2F:84:CA wlan0mon 

![refresca la página para cargar el imágen](imagen/kali6.png)

>airodump-ng -1 0 -a E8:DE:27:2F:84:CA wlan0mon

``````
