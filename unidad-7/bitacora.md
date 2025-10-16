
# Evidencias de la unidad 7

## Actividad 1  

**¿Qué URL de Dev Tunnels obtuviste? ¿Por qué crees que necesitamos usar esta URL en lugar de http://localhost:3000 o la IP local de tu computador para que el celular se conecte?**  
la url que me dió es https://js14dxnz-3000.use.devtunnels.ms/, debemos utilizar esa dirección en vez de http://localhost:3000 o la IP local, ya que el celular no puede acceder al localhost del computador.

**Describe brevemente qué hace npm install y npm start.**   
* El comando npm install sirve para descargar e instalar todo lo que el proyecto necesita para funcionar, según lo que está escrito en el archivo package.json.
* El comando npm start se usa para ejecutar el proyecto, normalmente iniciando el servidor o el programa principal que se indica en ese archivo.

**¿Qué mensajes observaste en la terminal del servidor al conectar el cliente de escritorio y el cliente móvil? ¿Eran diferentes los mensajes o identificadores?**   
Cuando se conectó primero el computador y luego el celular, el servidor mostró el mensaje “New client connected” para cada uno, pero con códigos diferentes, porque cada dispositivo tiene su propio socket ID.
**Fotos de prueba**   

<img width="640" height="640" alt="image" src="https://github.com/user-attachments/assets/1bdf8ace-6523-4957-80db-f7a6176eca06" />

**Describe el comportamiento observado: ¿Funcionó la interacción? ¿Hubo algún retraso (latencia)?**   
Cuando los conecté funcionó bastante bien, mi pc reaccionaba al instante a lo que se hacía en mi telefono (mover el dedo para cambiar de posición la bolita)

## Actividad 2  
**Explica con tus propias palabras: ¿Por qué es necesario Dev Tunnels en este escenario y cómo funciona conceptualmente?**  
Dev Tunnels se usa porque el servidor corre en localhost:3000, y esa dirección solo funciona en mi computador. El celular no puede entrar ahí, ya que para él “localhost” es su propio equipo. Con Dev Tunnels se puede crear una conexión segura y sencilla entre los dos dispositivos sin enredos con IPs ni redes.

**Describe la función de touchMoved() y por qué se usa la variable threshold en el cliente móvil.**   
touchMoved() se activa cuando toco y muevo el dedo en la pantalla. Guarda las coordenadas del movimiento y las manda al servidor con Socket.IO, que después las envía al computador para que se vean los cambios. También tiene un límite para no enviar movimientos muy pequeños y así no llenar el túnel con muchas señales.

**Compara brevemente Dev Tunnels con simplemente usar la IP local. ¿Cuáles son las ventajas y desventajas de cada uno?**  
| **Método**      | **Ventajas**                                                                                                 | **Desventajas**                                                                                                                            |
| --------------- | ------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------ |
| **IP local**    | Es más rápida porque está en la misma red y no depende tanto de internet.                                    | Solo funciona si el compu y el celular están conectados al mismo Wi-Fi. Además, puede dar problemas con el firewall y no es muy segura.    |
| **Dev Tunnels** | Permite conectarse desde cualquier lugar, usa conexión **HTTPS** segura y evita configuraciones complicadas. | Puede tener más retraso al enviar los datos, depende más del internet y tiene un límite de usuarios que pueden conectarse al mismo tiempo. |

**Coloca en tu bitácora capturas de pantalla del sistema completo funcionando. Esto lo puedes hacer abriendo tanto el mobile como el desktop en tu computador y tomando una captura de pantalla de todos los involucrados (celular, computador y terminal).**  
**En el pc**   
<img width="323" height="683" alt="image" src="https://github.com/user-attachments/assets/6e82c0bb-d692-4c9a-8d4a-0c4331bfac6f" />       

**En el cel**  
<img width="323" height="683" alt="image" src="https://github.com/user-attachments/assets/3da49774-ee78-4997-88eb-0c7151be2625" />

## Actividad 03   
**¿Cuál es la función principal de express.static(‘public’) en este servidor? ¿Cómo se compara con el uso de app.get(‘/ruta’, …) del servidor de la Unidad 6?**  
express.static('public') sirve para que el servidor muestre automáticamente los archivos que están en la carpeta public. En la unidad 6 tocaba escribir una por una las rutas de las vistas para poder verlas.

**Explica detalladamente el flujo de un mensaje táctil: ¿Qué evento lo envía desde el móvil? ¿Qué evento lo recibe el servidor? ¿Qué hace el servidor con él? ¿Qué evento lo envía el servidor al escritorio? ¿Por qué se usa socket.broadcast.emit en lugar de io.emit o socket.emit en este caso?**   
* Cuando muevo el dedo en la pantalla del celular, la función touchMoved() lo detecta y manda los datos al servidor con socket.emit('message', touchData).  
* El servidor recibe ese mensaje con socket.on('message', ...) y lo vuelve a enviar a los demás usando socket.broadcast.emit('message', message).  
* En el celular solo se muestra el mensaje en la consola, pero en el computador el circulito se mueve según las coordenadas que llegan.  
* Se usa broadcast.emit porque manda el mensaje a todos menos al celular que lo envió; io.emit lo mandaría a todos y socket.emit solo al mismo celular.

**Si conectaras dos computadores de escritorio y un móvil a este servidor, y movieras el dedo en el móvil, ¿Quién recibiría el mensaje retransmitido por el servidor? ¿Por qué?**   
Si tengo dos computadores con el programa de escritorio y un celular, cuando muevo el dedo en el celular, los dos computadores reciben el mensaje, porque el servidor se lo manda a todos los que están conectados, menos al que lo envió.

**¿Qué información útil te proporcionan los mensajes console.log en el servidor durante la ejecución?**    
Muestra cuándo un cliente se conecta, la posición del toque que detecta y también si alguien se desconecta. Todo eso ayuda a saber en qué parte puede estar fallando el código.










