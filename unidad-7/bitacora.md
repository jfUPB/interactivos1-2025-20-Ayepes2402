
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

## Actividad 4  
**Realiza un diagrama donde muestres el flujo completo de datos y eventos entre los tres componentes: móvil, servidor y escritorio. Puedes ilustrar con un ejemplo de coordenadas táctiles (x, y) y cómo viajan a través del sistema.**

<img width="378" height="665" alt="image" src="https://github.com/user-attachments/assets/2405a42c-62c3-4362-a4bf-6fbbbce768a2" />

## Apply 
**Has analizado cómo el móvil puede controlar el escritorio a través de un servidor y Dev Tunnels. Ahora es tu turno de ser creativo. Tomarás la base tecnológica y crearás una aplicación interactiva diferente, manteniendo la esencia: el touch del móvil como input principal. Diseña una aplicación interactiva que use el touch del móvil para controlar una visuales de tema musical de tu elección. Las visuales correrán en una aplicación de escritorio (desktop). Recuerda que ambas aplicaciones las construirás usando p5.js y utilizando el servidor Node.js como puente. Implementa tu diseño. Puedes usar IA generativa para ayudarte a escribir el código, pero primero debes hacer el diseño de lo que quieres. Incluye todos los códigos (servidor y clientes) en tu bitácora.**

**desktop html**
````html
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>🎵 Guitarra Interactiva - Pantalla</title>
<script src="https://cdn.jsdelivr.net/npm/p5@1.11.0/lib/p5.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/p5@1.11.0/lib/addons/p5.sound.min.js"></script>
<script src="https://cdn.socket.io/4.7.5/socket.io.min.js"></script>
<script src="sketch.js"></script>
<style>
      body {
        margin: 0;
        overflow: hidden;
        background-color: #000;
        font-family: "Segoe UI", sans-serif;
      }
 
      button {
        position: absolute;
        left: 50%;
        top: 50%;
        transform: translate(-50%, -50%);
        background: #1db954;
        color: white;
        border: none;
        padding: 15px 25px;
        font-size: 20px;
        border-radius: 10px;
        cursor: pointer;
      }
 
      button:hover {
        background: #17a74a;
      }
</style>
</head>
<body></body>
</html>
````
**mobile html**
````html
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>🎸 Guitarra Interactiva - Móvil</title>
<script src="https://cdn.jsdelivr.net/npm/p5@1.11.0/lib/p5.min.js"></script>
<script src="https://cdn.socket.io/4.7.5/socket.io.min.js"></script>
<script src="sketch.js"></script>
<style>
      body {
        margin: 0;
        overflow: hidden;
        background-color: #000;
        font-family: "Segoe UI", sans-serif;
      }
</style>
</head>
<body></body>
</html>
````
**sketch desktop**
````js
let socket;
let song;
let gifLeft, gifRight;
let isPlaying = false;
let started = false;
let pitchValues = [0.8, 0.9, 1, 1.1, 1.2, 1.3]; 
 
function preload() {
  song = loadSound("song.mp3");
  gifLeft = loadImage("bailarin1.gif");
  gifRight = loadImage("bailarin2.gif");
}
 
function setup() {
  createCanvas(windowWidth, windowHeight);
  socket = io();
 
  
  let startBtn = createButton("🎵 Iniciar experiencia");
  startBtn.position(width / 2 - 100, height / 2);
  startBtn.style("font-size", "20px");
  startBtn.style("padding", "15px");
  startBtn.style("border-radius", "10px");
  startBtn.style("cursor", "pointer");
  startBtn.mousePressed(() => {
    started = true;
    userStartAudio();
    startBtn.remove();
  });
 
  socket.on("stringPlayed", (data) => {
    if (!started) return;
    let pitch = pitchValues[data.string] || 1;
 
 
    if (!isPlaying) {
      song.loop();
      isPlaying = true;
    }
 
    
    song.rate(pitch);
  });
 
  socket.on("pauseSong", () => {
    if (isPlaying) {
      song.pause();
      isPlaying = false;
    }
  });
}
 
function draw() {
  background(0);
 
  if (!started) {
    fill(255);
    textAlign(CENTER, CENTER);
    textSize(24);
    text("Presiona para empezar 🎵", width / 2, height / 2 + 80);
    return;
  }
 
  if (isPlaying) {
    image(gifLeft, width * 0.1, height * 0.3, 300, 300);
    image(gifRight, width * 0.6, height * 0.3, 300, 300);
  } else {
    fill(255);
    textAlign(CENTER, CENTER);
    textSize(24);
    text("🎸 toca las cuerdas desde el celular 🎶", width / 2, height / 2);
  }
}
````
**mobile desktop**
````js
let socket;
let strings = [];
let numStrings = 6;
let activeString = -1;
let lastTouchTime = 0;
let idleTime = 3000;
let fadeAmount = 0; 
 
function setup() {
  createCanvas(windowWidth, windowHeight);
  socket = io();
 
  for (let i = 0; i < numStrings; i++) {
    let y = map(i, 0, numStrings - 1, height * 0.2, height * 0.8);
    strings.push({ y, waveOffset: 0 });
  }
}
 
function draw() {
  background(20);
  stroke(255);
  strokeWeight(3);
  noFill();
 
  let now = millis();
  if (now - lastTouchTime > idleTime) {
    socket.emit("pauseSong");
  }
 
  for (let i = 0; i < strings.length; i++) {
    let s = strings[i];
    beginShape();
    for (let x = 0; x < width; x += 20) {
      let amp = (activeString === i) ? 20 : 2;
      let wave = sin((x + s.waveOffset) * 0.05) * amp * fadeAmount;
      vertex(x, s.y + wave);
    }
    endShape();
    s.waveOffset += 5;
  }
 
  fill(255);
  textAlign(CENTER, CENTER);
  textSize(22);
  text("🎸 toca una cuerda 🎶", width / 2, 40);
 
 
  if (activeString === -1 && fadeAmount > 0) {
    fadeAmount -= 0.2;
  }
  fadeAmount = constrain(fadeAmount, 0, 1);
}
 
function touchStarted() {
  lastTouchTime = millis();
  let t = touches[0];
  for (let i = 0; i < strings.length; i++) {
    let s = strings[i];
    if (abs(t.y - s.y) < 30) {
      activeString = i;
      fadeAmount = 1; 
      socket.emit("stringPlayed", { string: i });
    }
  }
  return false;
}
 
function touchEnded() {
  activeString = -1;
  socket.emit("stopString");
  return false;
}
````












