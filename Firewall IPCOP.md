Este software es bastante antiguo, pero esta muy bien para entender y poder aprender la configuración de un firewall a medio bajo

Vamos al sitio web: https://www.ipcop.org/download.html y hacemos clic en - [Latest installation CD (i486 2.1.8)](http://sourceforge.net/projects/ipcop/files/IPCop/IPCop%202.1.8/ipcop-2.1.8-install-cd.i486.iso)

Vamos a utilizar vmware para virtualizar esta infraestructura y segimos estos pasos 
1. New virtual machine
2. Seleccionamos la iso
 ![[Pasted image 20260423171639.png]]

3. En Operating system seleccionamos linux y la version de 3 linux kernel
![[Pasted image 20260423171947.png]]

4. Dejamos todas las opciones en predeterminadas hasta el tipo de disco ya que va a ser un firewall de bajos recursos
5. El tipo de disco que seleccionaremos será el SATA
6. Seguimos poniendo los apartados predeterminados hasta llegar al apartado de "Listos para crear maquina virtual", en este paso le daremos al botón de customize hardware
  ![[Pasted image 20260423172507.png]]
  7. Ya que la red que vamos a montar seria esta
![[Pasted image 20260423174214.png]]
Sabiendo que todo lo que entre desde la puerta de enlace el firewall va a estar haciendo un MITM

8. Claro como podemos ver tiene dos interfaces entonces en tendremos que tener una interfaz que nos muestre lo siguiente en virtual network preference
![[Pasted image 20260423174630.png]]

![[Captura de pantalla 2026-04-23 180257.png]]
![[Captura de pantalla 2026-04-23 180303.png]]

Aqui estarían las vlan y quitamos el use local DHCP service

9. Ahora en setting cambiamos las setting de la maquina virtual y l añadimos un adaptador y generamos mac para cada interfaz de red y tenerlas apuntadas para mas adelante mi nat es 00:50:56:23:41:41 y mi host-only es 00:0C:29:69:62:C6
![[Pasted image 20260423180952.png]]
10. Añadimos un nuevo adptador de red en host-only
  ![[Pasted image 20260423181212.png]]

#### Ahora seguimos con la configuración del firewall
1. Idima que queremos
2. Idioma del teclado
3. Zona Horaria
4. Introducir fecha y hora muy importante para la automatizacion y despliges de tareas de tareas 
5. Seleccionamos el disco duro y ponemos la instalacion en disco, la otra opción es memoria flash que sería con el uso de un pendrive
6. Saltar las opciones de Disquete o llave usb
7. siguiente parametros a elección hasta Interfaz red Roja que la configuraremos en DHCP
  ![[Pasted image 20260423182242.png]]
  8. Ahora tendremos la asignación de tarjetas Rojo WAN Verde LAN (Yo como hice tres tarjetas pondré una en azul) Sabremos cual es cual gracias a que apuntamos las MAC de cada tarjeta y a cual pertenecian
![[Pasted image 20260423182622.png]]
 Así en las demás
 9. Poner las ip de las interfaces 
   ![[Pasted image 20260423183449.png]]
   10. Saltamos la opción de DNS
   11. Hacemos el rango de DHCP dando al espacio para activar el servicio
   12. Ahora definimos las contraseñas importante acordarse
Y asi terminaria nuestro Firewall, entramos con el login root y la contraseña puesta anteriormente
![[Pasted image 20260423184215.png]]

En nuestro kali entramos a la red en la interfaz para tener conectividad (Yo entro en mi Wnet1)
![[Pasted image 20260423201720.png]]
Y por ultimo vemos la conectividad con ping, escaneo de puerto con nmap y vemos la web en el navegador
![[Pasted image 20260423202104.png]]

Podemos ver los puertos gracias a que estamos en la lan pero si estuviesemos fuera de la red y quisiéramos hacer una petición el firewall nos bloquearía.

Asi es como se monta un firewall, este modelo sule dar fallos asi que no se recomienda usarlo profesionalmente pero para aprender esta genial.

