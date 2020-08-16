# Redes 1 - Practica 1

El proposito de esta practica es configurar y administrar los dispositivos de una infraestructura de red pequeña para conocer el funcionamiento basico de estos dispositivos. 

## Topologia

La topologia consta de 1 Router, 2 switches, 3 VPCS y 1 maquina virtual. Toda la informacion se detalla en el enunciado de la practica (Practica1.pdf)

<p align="center">
    <img src="https://user-images.githubusercontent.com/30850990/90328324-c39a3200-df58-11ea-8f4d-1514ce877941.JPG" width="800px" height="418px">
</p>

## Configuracion

Para proceder a configurar las vpcs y el router, los iniciamos y damos doble click sobre su icono y esto nos abrira una consola (PuTTY) que ya viene instalada en GNS3.

Comandos a utilizar para configurar las VPCs:

* Para configurar la ip <br/>
  ``` ip <dir_ip> <mask> <gateway> ```
* Para ver la configuracion y cercionarnos que la ip fue asignada <br/>
  ``` sh ip ```
* Para guardar los cambios y que no se borren cuando se apague la maquina <br/> 
 ``` save ```                

### **PC1**
<br/>
<p>
    <img src="https://user-images.githubusercontent.com/30850990/90329108-03641800-df5f-11ea-926c-bc891a8cfed0.JPG" width="400px">
</p>

### **PC2**
<br/>
<p>
    <img src="https://user-images.githubusercontent.com/30850990/90328838-ec242b00-df5c-11ea-918b-605da904135d.JPG" width="400px">
</p>

### **PC3**
<br/>
<p>
    <img src="https://user-images.githubusercontent.com/30850990/90328845-fa724700-df5c-11ea-888e-75c0895db3d2.JPG" width="400px">
</p>

### **VM**
Para la maquina virtual el proceso es un poco diferente pero nada complicado, cuando la encendamos tendremos la siguiente interfaz:

<p>
    <img src="https://user-images.githubusercontent.com/30850990/90328966-fbf03f00-df5d-11ea-9956-e8bbc7f60f37.JPG" width="400px" >
</p>

En el menu de abajo buscaremos el panel de control

<p>
    <img src="https://user-images.githubusercontent.com/30850990/90329446-2f34cd00-df62-11ea-9051-d9fe8782c9a3.JPG" width="400px" >
</p>

Presionaremos la opcion de 'Network'
<p>
    <img src="https://user-images.githubusercontent.com/30850990/90329460-52f81300-df62-11ea-947c-6d78e7576e52.JPG" width="400px" >
</p>

Y en el menu que nos abra, ingresaremos la ip que deseamos asignar. Cuando presionemos 'apply' esta nos asignara la direccion de red de manera automatica.

<p>
    <img src="https://user-images.githubusercontent.com/30850990/90329464-57bcc700-df62-11ea-8a8b-892c50dcbd90.JPG" height="350px">
    <img src="https://user-images.githubusercontent.com/30850990/90329466-59868a80-df62-11ea-97be-0f530073b685.JPG" height="350px">
</p>

*Nota: La configuracion de la maquina virtual no se puede guardar asi que este proceso se tiene que realizar cada vez que se inicie. Cabe resaltar que no toma mas de 2 minutos.*

### **Router**

De la misma manera que con las vpcs, ya iniciado el router, damos doble click sobre su icono y esto nos abrira una consola. 

Comandos a utilizar para configurar el router:
* Entra al menu de configuracion del router <br/>
  ```conf t (configure terminal)```
* Entra a la configuracion de la interfaz establecida <br/>
  ```int f<n>/<n>```
* Asigna una ip a la interfaz <br/>
  ```ip address <ip> <mask>```
* Regresar al menu anterior <br/>
  ```exit```
* Muestra un resumen de las interfaces <br/>
  ```sh ip int brief (show ip interface brief)```
* Salir de todas las configuraciones <br/>
  ```end```
* Comando para guardar <br/>
  ```wr (write)```

<p>
Iniciamos con el comnado  <strong>sh ip int brief</strong> para mostrar el estado actual de las interfaces. <br/>
<img src="https://user-images.githubusercontent.com/30850990/90330593-25fc2e00-df6b-11ea-9a77-d873e6530d9d.JPG" width="500px">
</p>

<p>
Proseguimos con el comando <strong>conf t</strong> para entrar al menu de configuracion del router. Seleccionamos una interfaz con el comando <strong>int f< n >/< n > </strong> y procedemos a establecerle una ip con el comando <strong>ip address < ip > < mask > </strong> (Este proceso se tiene que realizar con las dos interfaces)  <br/>
<img src="https://user-images.githubusercontent.com/30850990/90330452-00baf000-df6a-11ea-9759-99b84069b89e.JPG" width="500px">
</p>

<p>
Volvemos a usar el comando <strong>sh ip int brief</strong> para mostrar el estado de las interfaces luego de la configuracion. <br/>
<img src="https://user-images.githubusercontent.com/30850990/90330458-0b758500-df6a-11ea-9142-323f5ef70b0f.JPG" width="500px">
</p>

<p>
Por ultimo usamos el comando <strong>wr</strong> para guardar los cambios en el router. <br/>
<img src="https://user-images.githubusercontent.com/30850990/90330455-09abc180-df6a-11ea-8f54-02bcb393300d.JPG" >
</p>
<br/>

Para comprobar que la configuracion realizada este correcta haremos ping de unas vpcs a otras, a la maquina virtual y tambien al router. 

- PC1 - PC3 <br/>
![vpc1-ping3](https://user-images.githubusercontent.com/30850990/90330672-e550e480-df6b-11ea-9f55-d4c3bd5fef25.JPG)
- PC1 - VM <br/>
![vpc1-pingvm](https://user-images.githubusercontent.com/30850990/90330673-e5e97b00-df6b-11ea-9b3d-40450702ff24.JPG)

- PC2 - PC1 <br/>
![vpc2-ping1](https://user-images.githubusercontent.com/30850990/90330677-e97d0200-df6b-11ea-8d42-07d1fc2e3701.JPG)
- PC2 - VM <br/>
![vpc2-pingvm](https://user-images.githubusercontent.com/30850990/90330676-e97d0200-df6b-11ea-827e-bbfd4d345e58.JPG)


- PC3 - PC2 <br/>
![vpc3-ping2](https://user-images.githubusercontent.com/30850990/90330685-f00b7980-df6b-11ea-9275-cb3cd0ce7abb.JPG)
- PC3 - Router <br/>
![vpc3-pingR](https://user-images.githubusercontent.com/30850990/90330686-f0a41000-df6b-11ea-9555-d2cb7c53c519.JPG)

- VM - PC1 <br/>
![vm-ping1](https://user-images.githubusercontent.com/30850990/90339174-50baa680-dfac-11ea-9c1a-209b27712ee8.JPG)

- VM - PC2 <br/>
![vm-ping2](https://user-images.githubusercontent.com/30850990/90339173-50221000-dfac-11ea-8c2f-e3690e9a3513.JPG)


## Glosario
1. **Router**: Es un dispositivo que proporciona conectividad a nivel de red. Es capaz de conectar con otras redes o subredes y enviar paquetes de datos a traves de ellas.
2. **Switch**: Dispositivo que permite la conectividad de equipos **de una misma red**. 
3. **VPC**: Es un ordenador virtual que funciona como el punto de inicio y final de las transferencias de datos. Estas poseen una direccion IP que puede ser asignada manualmente o automaticamente.
4. **VM (virtual machine)**: Es un software que simula un sistema de computacion y puede ejecutar programas como si fuera una computadora real.
5. **Mask (mascara de red)**: Es una combinación de bits que sirve para delimitar el ámbito de una red de ordenadores. Su función es indicar a los dispositivos qué parte de la dirección IP es el número de la red, incluyendo la subred, y qué parte es la correspondiente al host.
6. **Gateway (puerta de enlace)**: Es el dispositivo que actúa de interfaz de conexión entre dispositivos y también posibilita compartir recursos entre dos o más ordenadores.
7. **Direccion IP**: Es un conjunto de números que identifica, de manera lógica y jerárquica, a una Interfaz en la red de un dispositivo que utilice el protocolo (Internet Protocol), que corresponde al nivel de red del modelo TCP/IP.
8. **PuTTY**: Es un cliente SSH, Telnet y TCP raw con licencia libre.
9. **TCP/IP**: es un modelo usado para comunicaciones en redes y como todo protocolo, describe un conjunto de guías generales de operación para permitir que un equipo pueda comunicarse en una red. Provee conectividad de extremo a extremo especificando cómo los datos deberían ser formateados, direccionados, transmitidos, enrutados y recibidos por el destinatario.
10. **Telnet(Teltype Network)**: Es el nombre de un protocolo de red que nos permite acceder a otra máquina para manejarla remotamente.

# Herramientas utlizadas
* [GNS3](https://www.gns3.com/)
* [VMWare](https://www.vmware.com/latam/products/workstation-pro.html)
* [Tiny-Linux](http://tinycorelinux.net/)

# Autor
Raul Xiloj