# flow4-NodeRed
Este repositorio contiene el flow 4 del curso de NodeRed. visto en los contenidos de codigoIoT

## Introducción

Este flow consiste en un tablero que presente la información de temperatura y humedad locales. Este flow recibe la información por MQTT con un broker local. Se usarán los nodos siguentes

- Mqtt-in

   > El nodo **mqtt-in** se conecta a un broker de mqtt y se suscribe al tema especificado
- Json

   > El nodo **json** convierte una string de un json a su objeto de JavaScript y viceversa
- Function
 
   > El nodo **function** ejecuta una función de JavaScript en el mensaje que esta siendo recibido 
- Los nodos **guage** y **chart** de los nodos dashboard

### Material Necesario

Para realizar este ejercicio necesitaras lo siguente

- [Ubuntu 20.04](https://ubuntu.com/download/desktop)
- [NodeJs](https://nodejs.org/en/)
  - [NPM](https://www.npmjs.com/)
  - [NodeRed](https://nodered.org/)
  - Nodos Dashboard
      > Se pueden instalar desde Manage palette en node red, En este caso instalamos **node-red-dashboard**
  - [Mosquitto](https://mosquitto.org/)

### Material de referencia

- [Instalación de Virtual Box](https://edu.codigoiot.com/course/view.php?id=810)
  - [Instalación de Ubuntu 20.04](https://edu.codigoiot.com/course/view.php?id=812)
- [Instalación de NodeRed](https://edu.codigoiot.com/course/view.php?id=817)
- [Introducción a NodeRed](https://edu.codigoiot.com/course/view.php?id=278)
- [Introducción a Mosquitto](https://edu.codigoiot.com/course/view.php?id=851)

# Instrucciones

## Requisitos previos

1. Tener instalado todo el software listado en el **Material necesario**
2. Arrancar NodeRed escribiendo el comando `node-red` en la terminal
3. Abrir aplicacion de NodeRed en un navegador con la dirección ["http://localhost:1880"](http://localhost:1880/#flow/d0319225ca32761b)

## Instrucciones de ejecución

1. Se arrastran los siguentes nodos
     - mqtt-in
     - json
     - function x2
     - chart
     - guage x2

2. Conecta los nodos como se muestra en la imagen de los resultados
3. Configura el nodo de mqtt-in como se muestra en la siguente imagen
   ![configuraciones de mqtt-in](https://github.com/davidGalaviz/flow4-NodeRed/blob/main/Captura%20de%20pantalla%20de%202022-08-29%2014-02-47.png)
4. Configura la propiedad action del json a "Siempre convertir a un objeto de JavaScript"
5. En el nodo 1 de function agrega el siguente codigo `msg.payload = msg.payload.temp;` `msg.topic = "Temperatura"` `return msg;`
6. En el nodo 2 de function agrega el siguente codigo `msg.payload = msg.payload.hum;` `msg.topic = "Humedad"` `return msg;`
7. Configura los nodos chart y guage
8. Enviar por MQTT un mensaje que contenga un JSON con las variables ID, temp y hum
9. Se guarda el flow oprimiendo el botón **Deploy**

# Resultados 

El flow debera verse como el flow de la siguiente imagen

![resultados del flow](https://github.com/davidGalaviz/flow4-NodeRed/blob/main/Captura%20de%20pantalla%20de%202022-08-29%2012-38-20.png)

Entra a [http://localhost:1880/ui](http://localhost:1880/ui/#!/0?socketid=OGWdowKrOPcSz4pfAAAD) para ver el Dashboard

![resultados en el Dashboard](https://github.com/davidGalaviz/flow4-NodeRed/blob/main/Captura%20de%20pantalla%20de%202022-08-29%2012-39-42.png)

## Evidencias

[Repositorio](https://github.com/davidGalaviz/flow4-NodeRed)

# Creditos

Desarrollado por David Galaviz

[GitHub](https://github.com/davidGalaviz)


