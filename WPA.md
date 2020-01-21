# hack-wifi WPA

Si usamos el cifrado WPA es totalmente seguro de los ataques? Vamos a intentar romper la contraseña de una red wifi con cifrado WPA. No pongas contraseña muy larga para este práctica, te vas a tardar bastante en descifrarlo.

![refresca la página para cargar el imágen](imagen/wpa0.png)

Para empezar abrimos el terminal y los 4º primeros pasos son iguales que el [Hackear wifi wep](https://nswhuei.github.io/hack-wifi/ActividadRQ3.1).


![refresca la página para cargar el imágen](imagen/wpa1.png)

Empezamos a capturar los paquetes de la red wifi, para descifrar la contraseña del wpa necesitamos un paquete especial: "handshake". Para ello necesitamos que algún equipo de la red se conecte de nuevo, podemos esperar o usar siguiente comando para desconectar un equpo de la red.

>aireplay-ng -0 2 -a 21:7F:20:02:63:B6 -c F8:87:F1:BD:76:24 wlan1mon

```-0``` El código de empezar el ataque de "Deautenticación". [Aireplay](https://www.aircrack-ng.org/doku.php?id=es:aireplay-ng)

```-a``` El bssid del router

```-c``` El bssid del equipo que vas a desconectar
