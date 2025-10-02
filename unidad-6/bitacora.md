
# Evidencias de la unidad 6  
## Actividad 01  

**¿Qué ocurrió en la terminal cuando ejecutaste npm install? ¿Cuál crees que es su propósito?**      
- Creo que descargó cosas para iniciar el archivo    

<img width="660" height="660" alt="image" src="https://github.com/user-attachments/assets/86ef234b-8942-4cca-8378-d130ad4c8833" />      

**¿Qué mensaje específico apareció en la terminal después de ejecutar npm start? ¿Qué indica este mensaje?**     
- Cuando aparece el mensaje `Server is listening on http://localhost:3000` quiere decir que el servidor arrancó sin problemas y está usando el puerto 3000 en mi computadora. Esto ocurre porque al ejecutar el comando start que está en el package.json, se pone en marcha el archivo server.js con Node.js.   

<img width="663" height="663" alt="image" src="https://github.com/user-attachments/assets/a2278086-70ca-4d69-9f96-f3d2d3e92ea2" />    


**Describe lo que ves inicialmente en page1 y page2 en tu navegador.**    
- Me aparece un mensaje de conectando para luego aparecer dos circulos rojos los cuales estáan conectados y se siguen cuando mueves la ventana
   
<img width="660" height="660" alt="image" src="https://github.com/user-attachments/assets/31c12b60-4666-4da3-aff3-a9801136bee4" />


**¿Qué mensajes aparecieron en la terminal del servidor cuando abriste page1 y page2?**   
- El servidor reconoce cada conexión, recibe la información de la ubicación de las ventanas y va mostrando cómo se sincronizan, hasta que ambas quedan totalmente conectadas y coordinadas.   

<img width="660" height="660" alt="image" src="https://github.com/user-attachments/assets/13f0e167-82b4-4709-a8e2-5345fa4a147c" />     


**Describe qué sucede en ambas páginas del navegador cuando mueves una de las ventanas. ¿Cambia algo visualmente? ¿Qué mensajes aparecen (si los hay) en la consola del navegador (usualmente accesible con F12 -> Pestaña Consola) y en la terminal del servidor?**   
- En las dos páginas los círculos parecen enlazarse, y al mover las pestañas sus ejes se acomodan como si se estuvieran siguiendo uno al otro.   


## Actividad 02  

**Piensa en cómo te conectas a Internet en casa o en la Universidad. ¿Usas Wi-Fi? ¿Un cable de red? Eso es simplemente tu “rampa de acceso” a la gran red de carreteras. ¿Qué pasaría si esa rampa se corta? Anota tus ideas.**  
- Si se corta esa rampa de acceso, me quedo sin Internet, entonces no podría chatear, buscar información ni entrar a clases virtuales. Sería como quedar desconectado del mundo hasta que vuelva la señal o use otra forma de conectarme.   

>**Indagación:**
>
>Una "rampa de acceso a internet" generalmente se refiere a una conexión directa y segura a servicios en la nube (cloud on-ramp), que bypassa el internet público para empresas, ofreciendo >mayor rendimiento y seguridad, o a la accesibilidad digital, que son las tecnologías y diseños (como las rampas para sillas de ruedas o el texto alternativo en imágenes) que permiten a >todas las personas con o sin discapacidad acceder y utilizar los servicios de internet.

**¿Puedes identificar otros ejemplos de relaciones Cliente-Servidor en tu vida diaria (no necesariamente digitales)? Por ejemplo, al pedir comida en un restaurante. ¿Quién es el cliente y quién el servidor? ¿Qué se pide y qué se entrega?**   
- puede ser en una estación de gasolina: el cliente es la persona que llega con su carro y el servidor es el trabajador de la estación que recibe la solicitud y entrega el servicio al poner la gasolina.  

**Toma la URL de tu sitio web favorito. Intenta identificar el protocolo, el nombre de dominio y la ruta (si la hay). ¿Qué crees que pasa si solo escribes el nombre de dominio (ej. www.google.com) sin una ruta específica? ¿Qué “página por defecto” crees que te envía el servidor**  
- La página que elegí es https://www.roblox.com/es/home  
* **Protocolo:** https  indica que la conexión es segura.   
* **Nombre de dominio:** www.roblox.com  es la dirección del sitio web.
* **Ruta:** /es/home señala la sección en español de la página de inicio.
- A lo mejor cuando pongo solo //www.roblox.com me manda a los juegos o a ningún lado

**Compara HTTP con los protocolos seriales que usaste. ¿Qué similitudes encuentras? ¿Qué diferencias clave ves? ¿Por qué crees que HTTP necesita ser más complejo que un simple envío de bytes como hacías con el micro:bit?**   
- Creo que tanto ASCII como HTML usan texto que se puede leer cuando se mandan los datos. La diferencia es que HTTP no solo va por un cable directo, sino que necesita Internet, servidores y funcionar en cualquier dispositivo, lo que lo hace más complicado.

**¿Por qué crees que HTTP necesita ser más complejo que un simple envío de bytes como hacías con el micro:bit?**    
- Porque HTTP no solo manda bytes, también organiza la información para que pueda viajar por Internet, llegue al servidor correcto y sea entendida en cualquier dispositivo. Además, permite que haya respuestas, seguridad y que funcione con muchas páginas al mismo tiempo, por eso tiene que ser más complejo que solo enviar datos directos como con el micro:bit.  

**Piensa en una página web simple, como un formulario de login. ¿Qué parte crees que es HTML (ej. los campos de texto, el botón)?**  
- El HTML es lo que arma la página: las casillas para usuario y contraseña, los textos y el botón para entrar.  

**¿Qué parte es CSS (ej. el color del botón, el tipo de letra)?**  
- es lo que le da estilo a la página, como el color del botón, el tamaño y tipo de letra, o el fondo del formulario.  

**¿Qué parte es JavaScript (ej. la comprobación de si escribiste algo antes de enviar, el mensaje de “contraseña incorrecta” que aparece sin recargar la página)?**  
- El JavaScript se encarga de la parte interactiva, como revisar si escribiste algo antes de enviar, mostrar un aviso de “contraseña incorrecta” sin recargar la página o hacer que el botón funcione al dar clic. 

**Compara el bucle draw() de p5.js con este modelo de “esperar a que algo pase y reaccionar”.**    
| **draw() en p5.js**                               | **Esperar y reaccionar (eventos)**                        |
| ------------------------------------------------- | --------------------------------------------------------- |
| Se ejecuta de manera continua, cuadro por cuadro. | Solo corre cuando ocurre un evento (clic, tecla, etc.).   |
| Siempre está redibujando y revisando cambios.     | El programa se queda quieto hasta que algo pasa.          |
| Útil para animaciones y gráficos en movimiento.   | Útil para formularios, botones o interacciones puntuales. |

**¿Qué ventajas crees que tiene el modelo basado en eventos para una interfaz de usuario web?**  
- El modelo basado en eventos tiene la ventaja de que la página no está gastando recursos todo el tiempo, sino que solo reacciona cuando el usuario hace algo, como un clic o escribir. Eso hace que la interfaz sea más rápida, consuma menos energía y se sienta más ligera de usar.

**¿Sería eficiente tener un bucle draw() redibujando toda la página 60 veces por segundo si nada ha cambiado?**  
- No, no sería eficiente. Si la página se redibuja 60 veces por segundo sin que haya cambios, se gastarían recursos del procesador y batería innecesariamente.

**¿Por qué crees que podría ser útil usar JavaScript tanto en el cliente (navegador) como en el servidor? ¿Se te ocurre alguna ventaja para los desarrolladores?**   
- Es útil porque con JavaScript en el navegador se maneja lo que el usuario hace y ve, y en el servidor se controlan los datos y la lógica. La ventaja es que el programador usa el mismo lenguaje en los dos lados, lo que facilita aprender y trabajar más rápido.

**Resume con tus propias palabras la diferencia fundamental entre una comunicación HTTP tradicional y una comunicación usando WebSockets/Socket.IO. ¿En qué tipo de aplicaciones has visto o podrías imaginar que se usa esta comunicación en tiempo real?**  
- La diferencia es que en HTTP cada vez que quiero algo tengo que pedirlo de nuevo al servidor, mientras que con WebSockets/Socket.IO se abre una conexión que queda activa y permite que los datos viajen en tiempo real en las dos direcciones. Esto se usa en cosas como chats en línea, videojuegos multijugador, transmisiones en vivo o apps donde la información cambia al instante.

## Actividad 03  
**Detén el servidor si está corriendo. Cambia la primera ruta de /page1 a /pagina_uno. Inicia el servidor. Intenta acceder a http://localhost:3000/page1. ¿Funciona?**  

<img width="220" height="220" alt="image" src="https://github.com/user-attachments/assets/f49fbfd1-f391-46ee-97ff-c44a0230a67b" />  

- No

**Ahora intenta acceder a http://localhost:3000/pagina_uno. ¿Funciona?**   
<img width="259" height="220" alt="image" src="https://github.com/user-attachments/assets/56bebbe6-8192-410a-953d-3b0c651d9603" />

- Si

**¿Qué te dice esto sobre cómo el servidor asocia URLs con respuestas? Restaura el código.**  
Me indica que relaciona la URL con el nombre asignado para identificar qué debe utilizar.  

**Asegúrate de que el servidor esté corriendo (npm start). Abre http://localhost:3000/page1 en una pestaña. Observa la terminal del servidor. ¿Qué mensaje ves? Anota el ID.**  
````
A user connected - ID: lQehQqdq6j0AQkx3AAAB
````
**Abre http://localhost:3000/page2 en OTRA pestaña. Observa la terminal. ¿Qué mensaje ves? ¿El ID es diferente?**   
````
User disconnected - ID: jq9DJIanHZJIkP9FAAAB
````
- Si, el ID es diferente

**Cierra la pestaña de page1. Observa la terminal. ¿Qué mensaje ves? ¿Coincide el ID con el que anotaste?**  
````
A user connected - ID: lQehQqdq6j0AQkx3AAAB
````
- Si, coinciden ambos

**Cierra la pestaña de page2. Observa la terminal.**  
````
User disconnected - ID: jq9DJIanHZJIkP9FAAAB
````
- Si, coincide

**Inicia el servidor y abre page1 y page2. Mueve la ventana de page1. Observa la terminal del servidor. ¿Qué evento se registra (win1update o win2update)? ¿Qué datos (Data:) ves?**  
````
Mover Page1: Received win1update from ID: KJOROJ-q_VhNf1DwAAAB Data: { x: -4, y: 109, width: 237, height: 968 }
````
**Mueve la ventana de page2. Observa la terminal. ¿Qué evento se registra ahora? ¿Qué datos ves?**  
````
Mover Page2: Received win2update from ID: zHdk-5FsKF6bfvFnAAAF Data: { x: 937, y: 119, width: 159, height: 968 }
````

**Experimento clave: cambia socket.broadcast.emit(‘getdata’, page1); por socket.emit(‘getdata’, page1); (quitando broadcast). Reinicia el servidor, abre ambas páginas. Mueve page1. ¿Se actualiza la visualización en page2? ¿Por qué sí o por qué no? (Pista: ¿A quién le envía el mensaje socket.emit?). Restaura el código a broadcast.emit.**  
-Al modificar esa línea de código, la página 2 deja de recibir actualizaciones. Con socket.emit el dato solo se envía al mismo cliente, mientras que con broadcast.emit se comparte con todos los demás, menos con quien lo mandó.

**Detén el servidor. Cambia const port = 3000; a const port = 3001;. Inicia el servidor. ¿Qué mensaje ves en la consola? ¿En qué puerto dice que está escuchando? Intenta abrir http://localhost:3000/page1. ¿Funciona?**  
- No

**Intenta abrir http://localhost:3001/page1. ¿Funciona?**  
- Si

**¿Qué aprendiste sobre la variable port y la función listen? Restaura el puerto a 3000.**  
La variable port señala en qué puerto estará el servidor, y la función listen lo arranca en ese puerto en particular.  

## Actividad 04    

**Abre page2.html en tu navegador (con el servidor corriendo). Abre la consola de desarrollador (F12). Detén el servidor Node.js (Ctrl+C). Refresca la página page2.html. Observa la consola del navegador. ¿Ves algún error relacionado con la conexión? ¿Qué indica?**   

<img width="404" height="102" alt="image" src="https://github.com/user-attachments/assets/db01af8b-c706-41e9-8b03-30810babff7b" />   

- Hay un error en el GET de manager.js. Al reiniciar el servidor y refrescar, desaparece, mostrando que el cliente solo se comunica si el servidor está activo.

**Vuelve a iniciar el servidor y refresca la página. ¿Desaparecen los errores?**  
- Si

**Comenta la línea socket.emit(‘win2update’, currentPageData, socket.id); dentro del listener connect. Reinicia el servidor y refresca page1.html y page2.html. Mueve la ventana de page2 un poco para que envíe una actualización. ¿Qué pasó? ¿Por qué?**   

<img width="646" height="93" alt="image" src="https://github.com/user-attachments/assets/87e1e285-3216-4c19-9105-22fbfc640cb7" />

- Se perdió la comunicación  entre aambas páginas.

**Asegúrate de tener este console.log en page2.js. Abre ambas páginas. Mueve la ventana de page1. Observa la consola del navegador de page2. ¿Qué datos muestra?**   

<img width="289" height="223" alt="image" src="https://github.com/user-attachments/assets/540f7638-2f43-4a6b-931a-5b57a2a4c9c1" />   

**Mueve la ventana de page2. Observa la consola de page1. ¿Qué pasa? ¿Por qué?**   

<img width="311" height="145" alt="image" src="https://github.com/user-attachments/assets/39e103b8-5dfc-46a5-a78e-0b3f562b433e" />    

- Quiere decir que la app pasa los datos de una pestaña a la otra. Cuando mueves algo en una pestaña, se manda por socket.io y en la consola sale Received valid remote data.

**Observa checkWindowPosition() en page2.js y modifica el código del if para comprobar si el código dentreo de este se ejecuta. Mueve cada ventana y observa las consolas. ¿Qué puedes concluir y por qué?**

- El sistema solo manda información cuando hay un cambio de verdad, así no se envían datos de más.

**(¡Sé creativo!) Cambia el background(220) para que dependa de la distancia entre las ventanas. Puedes calcular la magnitud del resultingVector usando let distancia = resultingVector.mag(); y luego usa map() para convertir esa distancia a un valor de gris o color. background(map(distancia, 0, 1000, 255, 0)); (ajusta el rango 0-1000 según sea necesario). Inventa otra modificación creativa.**  
````cpp
let vector1 = createVector(currentPageData.x, currentPageData.y);
let vector2 = createVector(remotePageData.x, remotePageData.y);
let resultingVector = createVector(vector2.x - vector1.x, vector2.y - vector1.y);


let distancia = resultingVector.mag();

let bgColor = map(distancia, 0, 1000, 255, 0); 
background(bgColor);
````
````cpp
let circleSize = map(distancia, 0, 1000, 50, 300);
drawCircle(point1[0], point1[1], circleSize);
````
````cpp
function drawCircle(x, y, size = 150) {
    fill(255, 0, 0);
    ellipse(x, y, size, size);
}
````

<img width="660" height="660" alt="image" src="https://github.com/user-attachments/assets/438b0361-4d82-472c-bfc5-67023ec40d40" />    

<img width="660" height="660" alt="image" src="https://github.com/user-attachments/assets/cb2fd2c4-cf44-415f-9672-65a8481721a8" />   

- Entre más cerca esté uno de otro mas claro es el fondo y el radio del circulo depende de la distancia.

## Apply    

**Explica tu idea y realiza algunos bocetos.**   

- Me gustaria hacer unas ondas que entre más cerca esten mas alteradas esten y entre mas alejadas sean mas calmadas ademas de que cambien de color dependiendo de su aceleración.

**Bocetos**  

<img width="660" height="660" alt="image" src="https://github.com/user-attachments/assets/ae7eb6ff-ffa5-4511-9339-28ffc80d7799" />

<img width="660" height="660" alt="image" src="https://github.com/user-attachments/assets/e74240c9-a7f8-478d-9b46-29c3ceaf214c" />

**Implementa tu idea.**    

**server.js**
````cpp
const express = require('express');
const http = require('http');
const socketIO = require('socket.io');
const path = require('path');
const app = express();
const server = http.createServer(app); 
const io = socketIO(server); 
const port = 3000;

let page1 = { x: 0, y: 0, width: 100, height: 100 };
let page2 = { x: 0, y: 0, width: 100, height: 100 };
let connectedClients = new Map();
let syncedClients = new Set();

app.use(express.static(path.join(__dirname, 'views')));

app.get('/page1', (req, res) => {
    res.sendFile(path.join(__dirname, 'views', 'page1.html'));
});

app.get('/page2', (req, res) => {
    res.sendFile(path.join(__dirname, 'views', 'page2.html'));
});

io.on('connection', (socket) => {
    console.log('A user connected - ID:', socket.id);
    connectedClients.set(socket.id, { page: null, synced: false });
    
    socket.on('disconnect', () => {
        console.log('User disconnected - ID:', socket.id);
        connectedClients.delete(socket.id);
        syncedClients.delete(socket.id);
        socket.broadcast.emit('peerDisconnected');
        checkAndNotifySyncStatus();
    });

    socket.on('win1update', (window1) => { 
        if (isValidWindowData(window1)) {
            page1 = window1;
            connectedClients.set(socket.id, { page: 'page1', synced: false });
            socket.broadcast.emit('getdata', { data: page1, from: 'page1' });
            syncedClients.delete(socket.id);
            checkAndNotifySyncStatus();
        }
    });

    socket.on('win2update', (window2) => {
        if (isValidWindowData(window2)) {
            page2 = window2;
            connectedClients.set(socket.id, { page: 'page2', synced: false });
            socket.broadcast.emit('getdata', { data: page2, from: 'page2' });
            syncedClients.delete(socket.id);
            checkAndNotifySyncStatus();
        }
    });

    socket.on('requestSync', () => {
        const clientInfo = connectedClients.get(socket.id);
        if (clientInfo?.page === 'page1' && page2.width > 100) {
            socket.emit('getdata', { data: page2, from: 'page2' });
        } else if (clientInfo?.page === 'page2' && page1.width > 100) {
            socket.emit('getdata', { data: page1, from: 'page1' });
        }
    });

    socket.on('confirmSync', () => {
        syncedClients.add(socket.id);
        checkAndNotifySyncStatus();
    }); 
});

function isValidWindowData(data) {
    return data && 
            typeof data.x === 'number' && 
            typeof data.y === 'number' && 
            typeof data.width === 'number' && data.width > 0 &&
            typeof data.height === 'number' && data.height > 0;
}

function checkAndNotifySyncStatus() {
    const page1Clients = Array.from(connectedClients.values()).filter(info => info.page === 'page1');
    const page2Clients = Array.from(connectedClients.values()).filter(info => info.page === 'page2');
    
    const bothPagesConnected = page1Clients.length > 0 && page2Clients.length > 0;
    
    if (bothPagesConnected && syncedClients.size >= 2) {
        io.emit('fullySynced', true);
    } else {
        io.emit('fullySynced', false);
    }
}

server.listen(port, () => {
    console.log(`Server is listening on http://localhost:${port}`);
    console.log(`Open two windows:`);
    console.log(`- http://localhost:${port}/page1`);
    console.log(`- http://localhost:${port}/page2`);
});
````
**page1.html**  
````cpp
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Estanque Interactivo - Página 1</title>
    <script src="https://cdn.jsdelivr.net/npm/p5@1.11.0/lib/p5.min.js"></script>
    <script src="https://cdn.socket.io/4.7.5/socket.io.min.js"></script>
    <style>
        body {
            margin: 0;
            overflow: hidden;
            background-color: #1a1a40;
        }
    </style>
</head>
<body>
    <script defer src="page1.js"></script>
</body>
</html>
````
**page1.js**
````cpp
let currentPageData = {
    x: window.screenX,
    y: window.screenY,
    width: window.innerWidth,
    height: window.innerHeight
}

let previousPageData = { ...currentPageData }; 
let remotePageData = { x: 0, y: 0, width: 100, height: 100 };
let socket;
let isConnected = false;
let hasRemoteData = false;
let isFullySynced = false;
let maxDistance = 1500; 
let waveFactor = 0; 

function setup() {
    createCanvas(windowWidth, windowHeight);
    frameRate(60);
    socket = io();

    socket.on('connect', () => {
        isConnected = true;
        socket.emit('win1update', currentPageData);
        setTimeout(() => { socket.emit('requestSync'); }, 500);
    });

    socket.on('getdata', (response) => {
        if (response && response.data && isValidRemoteData(response.data)) {
            remotePageData = response.data;
            hasRemoteData = true;
            socket.emit('confirmSync'); 
        }
    });

    socket.on('fullySynced', (synced) => {
        isFullySynced = synced;
    });

    socket.on('peerDisconnected', () => {
        hasRemoteData = false;
        isFullySynced = false;
    });

    socket.on('disconnect', () => {
        isConnected = false;
        hasRemoteData = false;
        isFullySynced = false;
    });
}

function isValidRemoteData(data) {
    return data && 
            typeof data.x === 'number' && 
            typeof data.y === 'number' && 
            typeof data.width === 'number' && data.width > 0 &&
            typeof data.height === 'number' && data.height > 0;
}

function checkWindowPosition() {
    const newPageData = {
        x: window.screenX,
        y: window.screenY,
        width: window.innerWidth,
        height: window.innerHeight
    };

    if (newPageData.x !== previousPageData.x || newPageData.y !== previousPageData.y || 
        newPageData.width !== previousPageData.width || newPageData.height !== previousPageData.height) {

        currentPageData = newPageData;
        socket.emit('win1update', currentPageData);
        previousPageData = { ...currentPageData }; 
    }
}

function calculateWaveFactor() {
    let center1X = currentPageData.x + currentPageData.width / 2;
    let center1Y = currentPageData.y + currentPageData.height / 2;
    let center2X = remotePageData.x + remotePageData.width / 2;
    let center2Y = remotePageData.y + remotePageData.height / 2;
    
    let distValue = dist(center1X, center1Y, center2X, center2Y);
    let normalizedDist = constrain(distValue, 0, maxDistance);
    
    waveFactor = map(normalizedDist, 0, maxDistance, 1.0, 0.0);
    waveFactor = easeOutQuad(waveFactor); 
}

function easeOutQuad(t) {
    return t * t;
}

function drawWaves(factor) {
    let centerX = width / 2;
    let centerY = height / 2;
    
    noFill();
    strokeWeight(1 + factor * 5); 
    
    let hue = map(factor, 0, 1, 240, 360);
    let brightness = map(factor, 0, 1, 40, 100); 
    colorMode(HSB, 360, 100, 100);
    stroke(hue, 80, brightness, 0.9);

    let waveSpeed = map(factor, 0, 1, 0.5, 3.0); 
    let numRings = 10 + factor * 20; 
    let ringSpacing = map(factor, 0, 1, 100, 40);
    let amplitude = map(factor, 0, 1, 2, 40); 

    for (let i = 0; i < numRings; i++) {
        let radius = i * ringSpacing;
        let angleOffset = frameCount * 0.02 * waveSpeed + i * 0.5;
        
        let distRadius = radius + sin(angleOffset) * amplitude * map(i, 0, numRings, 1, 0.5);
        
        ellipse(centerX, centerY, distRadius * 2, distRadius * 2);
    }
    
    colorMode(RGB, 255);
    fill(255, 255, 255, 150 + factor * 105); 
    noStroke();
    ellipse(centerX, centerY, 50, 50);
}

function draw() {
    background(26, 26, 64);
    checkWindowPosition();
    
    if (!isConnected || !hasRemoteData || !isFullySynced) {
        showStatus('Esperando Conexión/Sincronización...');
        return;
    }

    calculateWaveFactor();
    
    drawWaves(waveFactor);
}

function showStatus(message, statusColor = null) {
    textSize(18);
    textAlign(CENTER, CENTER);
    noStroke();
    fill(0, 0, 0, 180);
    rectMode(CENTER);
    let textW = textWidth(message) + 40;
    let textH = 30;
    rect(width / 2, 30, textW, textH, 10);
    fill(statusColor || color(255, 180, 0));
    text(message, width / 2, 30);
}

function windowResized() {
    resizeCanvas(windowWidth, windowHeight);
}
````
**page2.html**
````cpp
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Estanque Interactivo - Página 2</title>
    <script src="https://cdn.jsdelivr.net/npm/p5@1.11.0/lib/p5.min.js"></script>
    <script src="https://cdn.socket.io/4.7.5/socket.io.min.js"></script>
    <style>
        body {
            margin: 0;
            overflow: hidden;
            background-color: #1a1a40;
        }
    </style>
</head>

<body>
    <script defer src="page2.js"></script>
</body>
</html>
````
**page2.js
````cpp
let currentPageData = {
    x: window.screenX,
    y: window.screenY,
    width: window.innerWidth,
    height: window.innerHeight
}

let previousPageData = { ...currentPageData }; 
let remotePageData = { x: 0, y: 0, width: 100, height: 100 };
let socket;
let isConnected = false;
let hasRemoteData = false;
let isFullySynced = false;
let maxDistance = 1500; 
let waveFactor = 0; 

function setup() {
    createCanvas(windowWidth, windowHeight);
    frameRate(60);
    socket = io();

    socket.on('connect', () => {
        isConnected = true;
        socket.emit('win2update', currentPageData);
        setTimeout(() => { socket.emit('requestSync'); }, 500); 
    });

    socket.on('getdata', (response) => {
        if (response && response.data && isValidRemoteData(response.data)) {
            remotePageData = response.data;
            hasRemoteData = true;
            socket.emit('confirmSync'); 
        }
    });

    socket.on('fullySynced', (synced) => {
        isFullySynced = synced;
    });

    socket.on('peerDisconnected', () => {
        hasRemoteData = false;
        isFullySynced = false;
    });

    socket.on('disconnect', () => {
        isConnected = false;
        hasRemoteData = false;
        isFullySynced = false;
    });
}

function isValidRemoteData(data) {
    return data && 
            typeof data.x === 'number' && 
            typeof data.y === 'number' && 
            typeof data.width === 'number' && data.width > 0 &&
            typeof data.height === 'number' && data.height > 0;
}

function checkWindowPosition() {
    const newPageData = {
        x: window.screenX,
        y: window.screenY,
        width: window.innerWidth,
        height: window.innerHeight
    };

    if (newPageData.x !== previousPageData.x || newPageData.y !== previousPageData.y || 
        newPageData.width !== previousPageData.width || newPageData.height !== previousPageData.height) {

        currentPageData = newPageData;
        socket.emit('win2update', currentPageData);
        previousPageData = { ...currentPageData }; 
    }
}


function calculateWaveFactor() {
    let center1X = currentPageData.x + currentPageData.width / 2;
    let center1Y = currentPageData.y + currentPageData.height / 2;
    let center2X = remotePageData.x + remotePageData.width / 2;
    let center2Y = remotePageData.y + remotePageData.height / 2;
    
    let distValue = dist(center1X, center1Y, center2X, center2Y);
    let normalizedDist = constrain(distValue, 0, maxDistance);
    
    waveFactor = map(normalizedDist, 0, maxDistance, 1.0, 0.0);
    waveFactor = easeOutQuad(waveFactor); 
}

function easeOutQuad(t) {
    return t * t;
}

function drawWaves(factor) {
    let centerX = width / 2;
    let centerY = height / 2;
    
    noFill();
    strokeWeight(1 + factor * 5); 
    
    let hue = map(factor, 0, 1, 240, 360); 
    let brightness = map(factor, 0, 1, 40, 100);
    colorMode(HSB, 360, 100, 100);
    stroke(hue, 80, brightness, 0.9);

    let waveSpeed = map(factor, 0, 1, 0.5, 3.0); 
    let numRings = 10 + factor * 20; 
    let ringSpacing = map(factor, 0, 1, 100, 40); 
    let amplitude = map(factor, 0, 1, 2, 40); 

    for (let i = 0; i < numRings; i++) {
        let radius = i * ringSpacing;
        let angleOffset = frameCount * 0.02 * waveSpeed + i * 0.5;
        
        let distRadius = radius + sin(angleOffset) * amplitude * map(i, 0, numRings, 1, 0.5);
        
        ellipse(centerX, centerY, distRadius * 2, distRadius * 2);
    }
    
    colorMode(RGB, 255);
    fill(255, 255, 255, 150 + factor * 105); 
    noStroke();
    ellipse(centerX, centerY, 50, 50);
}

function draw() {
    background(26, 26, 64); 
    checkWindowPosition();
    
    if (!isConnected || !hasRemoteData || !isFullySynced) {
        showStatus('Esperando Conexión/Sincronización...');
        return;
    }

    calculateWaveFactor();
    
    drawWaves(waveFactor);
}

function showStatus(message, statusColor = null) {
    textSize(18);
    textAlign(CENTER, CENTER);
    noStroke();
    fill(0, 0, 0, 180);
    rectMode(CENTER);
    let textW = textWidth(message) + 40;
    let textH = 30;
    rect(width / 2, 30, textW, textH, 10);
    fill(statusColor || color(255, 180, 0));
    text(message, width / 2, 30);
}

function windowResized() {
    resizeCanvas(windowWidth, windowHeight);
}
````
**Fotos**  
<img width="660" height="660" alt="image" src="https://github.com/user-attachments/assets/24a6928e-2ef6-486b-b38a-22aad79dab20" />  

<img width="660" height="669" alt="image" src="https://github.com/user-attachments/assets/8b82f432-0aad-40d9-8607-221dd87734f1" />








