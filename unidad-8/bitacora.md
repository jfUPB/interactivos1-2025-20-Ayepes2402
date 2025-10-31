
# Evidencias de la unidad 8

## Actividad 1     
En esta fase de la unidad vas a seleccionar un tema musical (o un concepto visual que desees explorar) que te guste y vas a definir el concepto de las visuales que quieres crear. Ten presente que estas visuales las controlarás en tiempo real desde un dispositivo móvil y el micro:bit.

**Tema musical o concepto visual**     
Voy a usar la canción [Blinding Lights](https://youtu.be/4NRXx6U8ABQ?si=RGnIdjpPAOti6s3U) de The Weeknd, porque tiene un ritmo muy marcado y me inspira a crear visuales de luces y colores que se mueven al compás.

**Referentes visuales**     
Me basé en luces neón, colores brillantes y fondos oscuros, parecidos a los videoclips de música electrónica o retro. También me inspiré en visuales que muestran círculos u ondas que vibran con el sonido.

**Concepto de las visuales**     
Mi idea es crear una animación donde círculos y líneas se mueven al ritmo de la canción. Cuando el sonido tiene más fuerza, los círculos crecen o cambian de color. El fondo será oscuro con tonos morados, azules y rojos para dar ese efecto de luces nocturnas.

**Control desde el móvil y el micro:bit**     
**Desde el celular:** tocar la pantalla cambia el color principal de las visuales.

**Desde el microbit:**    
* Botón A: pausa o reproduce la canción.      
* Botón B: cambia el tipo de visual (por ejemplo, círculos o barras).      
* Inclinando el micro:bit se puede cambiar la velocidad de los movimientos.

**Boceto telefono**   
<img width="497" height="601" alt="image" src="https://github.com/user-attachments/assets/22fdad87-282c-4708-b137-7d8548b1a045" />

**Boceto pc**  
<img width="1022" height="590" alt="image" src="https://github.com/user-attachments/assets/8a7b269a-415e-4aee-a394-069e3b1921e6" />

**Diagrama**  
<img width="677" height="982" alt="image" src="https://github.com/user-attachments/assets/9377837d-8298-440a-9162-9792fb500f52" />

## Actividad 02    
Ahora es momento de construir tu sistema interactivo. Recuerda que puedes usar IA generativa para ayudarte a escribir el código, pero primero debes hacer el diseño de lo que quieres. NO USES IA generativa para que te haga el diseño. Y una vez tengas el código generado por IA, debes entenderlo y analizar con detenimiento el código para asegurarte de que hace exactamente lo que tú quieres.

para hacer el codio primero le puse a gpt: podrias ayudarme a hacer el codigo para mi idea En esta fase de la unidad vas a seleccionar un tema musical (o un concepto visual que desees explorar) que te guste y vas a definir el concepto de las visuales que quieres crear. Ten presente que estas visuales las controlarás en tiempo real desde un dispositivo móvil y el micro:bit. Tema musical o concepto visual Voy a usar la canción Blinding Lights de The Weeknd, porque tiene un ritmo muy marcado y me inspira a crear visuales de luces y colores que se mueven al compás. Referentes visuales Me basé en luces neón, colores brillantes y fondos oscuros, parecidos a los videoclips de música electrónica o retro. También me inspiré en visuales que muestran círculos u ondas que vibran con el sonido. Concepto de las visuales Mi idea es crear una animación donde círculos y líneas se mueven al ritmo de la canción. Cuando el sonido tiene más fuerza, los círculos crecen o cambian de color. El fondo será oscuro con tonos morados, azules y rojos para dar ese efecto de luces nocturnas. Control desde el móvil y el micro:bit Desde el celular: tocar la pantalla cambia el color principal de las visuales. Desde el microbit: Botón A: pausa o reproduce la canción. Botón B: cambia el tipo de visual (por ejemplo, círculos o barras). Inclinando el micro:bit se puede cambiar la velocidad de los movimientos.

a lo cual me respondio 
<img width="108" height="386" alt="image" src="https://github.com/user-attachments/assets/cd77257f-6d23-482c-8af6-30ec458835c2" />

despues me puse a probar el código pero la verdad no me fue muy bien y no fui capaz de corregirlo, le pedi ayua a gpt y me decia que el código cumplia la idea pero no me ayudó mucho lo que me dijo

**Desktop html**
````js
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Visualizer - Desktop</title>

  <script src="https://cdn.jsdelivr.net/npm/p5@1.11.0/lib/p5.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/p5@1.11.0/lib/addons/p5.sound.min.js"></script>
  <script src="https://unpkg.com/@gohai/p5.webserial@^1/libraries/p5.webserial.js"></script>
  <script src="/socket.io/socket.io.js"></script>

  <style>
    html,body{margin:0;height:100%;background:#0f0420}
    #connectBtn{position:absolute;left:10px;top:10px;z-index:10}
  </style>
</head>
<body>
  <button id="connectBtn">Conectar micro:bit</button>
  <script src="sketch.js"></script>
</body>
</html>
````
**Desktop sketch.js**   
````cpp
let fft, song;
let audioStarted = false;
let colorMain = [255, 0, 255];
let visualMode = 'circles';
let speedFactor = 1.0;


let port;
let connectBtn;


let socket;

function preload() {
  soundFormats('mp3', 'ogg');
  song = loadSound('song.mp3');
}

function setup() {
  createCanvas(windowWidth, windowHeight);
  angleMode(DEGREES);

  fft = new p5.FFT();


  port = createSerial();
  connectBtn = select('#connectBtn');
  connectBtn.mousePressed(toggleSerial);


  socket = io();
  socket.on('connect', () => console.log('Socket connected'));
  socket.on('message', handleSocketMessage);


  port.on('data', serialEvent);
  port.on('open', () => console.log('Serial opened'));
  port.on('close', () => console.log('Serial closed'));
}

function draw() {
  background(12, 6, 25);

  if (!audioStarted) {
    drawStartScreen();
    return;
  }


  let spectrum = fft.analyze();
  let bass = fft.getEnergy('bass');
  let mid = fft.getEnergy('mid');
  let treble = fft.getEnergy('treble');


  push();
  translate(width/2, height/2);
  noFill();
  strokeWeight(6);

  let maxR = min(width, height) * 0.35 * speedFactor;
  for (let i = 0; i < 5; i++) {
    let r = maxR * (i+1)/5 * (1 + map(bass, 0, 255, 0, 0.5));
    let c = color(
      (colorMain[0] + i * 10) % 256,
      (colorMain[1] + i * 20) % 256,
      (colorMain[2] + i * 30) % 256
    );
    stroke(c);
    ellipse(0, 0, r*2, r*2);
  }
  pop();


  let binCount = 64;
  let bw = width / binCount;
  for (let i = 0; i < binCount; i++) {
    let val = spectrum[i];
    let h = map(val, 0, 255, 2, height * 0.35);
    let cx = i * bw;
    let c = color(
      (colorMain[0] + i * 3) % 256,
      (colorMain[1] + i * 2) % 256,
      (colorMain[2] + i * 1) % 256
    );
    noStroke();
    fill(c);
    rect(cx, height - h, bw * 0.8, h);
  }


  drawBottomUI(bass, mid, treble);
}

function drawStartScreen() {
  fill(255);
  textAlign(CENTER, CENTER);
  textSize(28);
  text('Toca para iniciar audio', width/2, height/2);
}

function drawBottomUI(bass, mid, treble) {
  push();
  fill(255, 200);
  textSize(16);
  textAlign(LEFT, CENTER);
  text('Estado: ' + (song.isPlaying() ? 'Reproduciendo' : 'Pausado'), 20, height - 25);
  text('Visual: ' + visualMode, 250, height - 25);
  text('Velocidad: ' + nf(speedFactor,1,2) + 'x', 460, height - 25);
  pop();
}

function mousePressed() {
  if (!audioStarted) {
    userStartAudio();
    song.loop();
    audioStarted = true;
  } else {
    if (song.isPlaying()) song.pause(); else song.play();
  }
}

function toggleSerial() {
  if (!port.opened()) {
    port.open('MicroPython', 115200);
    connectBtn.html('Desconectar micro:bit');
  } else {
    port.close();
    connectBtn.html('Conectar micro:bit');
  }
}


function serialEvent() {
  let s = port.readStringUntil('\n');
  if (!s) return;
  s = s.trim();
  if (s.length === 0) return;
  console.log('Serial:', s);



  if (s === 'A') {
    if (song.isPlaying()) song.pause(); else song.play();
  } else if (s === 'B') {
    if (visualMode === 'circles') visualMode = 'bars';
    else visualMode = 'circles';
  } else if (s === 'C') {
    flashColor();
  } else if (s[0] === 'T') {
    let val = parseInt(s.substring(1));
    if (!isNaN(val)) {
      speedFactor = map(val, 0, 100, 0.6, 2.0);
      speedFactor = constrain(speedFactor, 0.5, 3.0);
    }
  }
}

function flashColor() {
  let old = colorMain.slice();
  colorMain = [255, 220, 40]; // yellow burst
  setTimeout(() => { colorMain = old; }, 600);
}

function handleSocketMessage(data) {
  if (!data || !data.type) return;
  if (data.type === 'color' && data.hex) {
    let hex = data.hex.replace('#','');
    if (hex.length === 6) {
      colorMain = [parseInt(hex.substr(0,2),16),
                   parseInt(hex.substr(2,2),16),
                   parseInt(hex.substr(4,2),16)];
    }
  } else if (data.type === 'touch') {
    flashColor();
  } else if (data.type === 'yellowShift') {
    flashColor();
  }
}

function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
}
````
**Mobile html**  
`````js
<!-- public/mobile/index.html -->
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Mobile Controller</title>
  <script src="https://cdn.jsdelivr.net/npm/p5@1.11.0/lib/p5.min.js"></script>
  <script src="/socket.io/socket.io.js"></script>
  <style>html,body{margin:0;height:100%;}canvas{display:block;}</style>
</head>
<body>
  <script src="sketch.js"></script>
</body>
</html>
``````
**Mobile sketch.js**  
````cpp

let socket;
let currentColor = '#FF00FF';
let sending = false;

function setup() {
  createCanvas(windowWidth, windowHeight);
  background(20);
  socket = io();

  socket.on('connect', () => console.log('Connected mobile', socket.id));


  noLoop();
}

function draw() {
  background(40, 10, 60);
  textAlign(CENTER, CENTER);
  fill(220);
  textSize(20);
  text('Toca para cambiar color principal\nMantén presionado y arrastra para enviar toque', width/2, 40);


  let colors = ['#FF0066','#FFCC00','#00FFFF','#7B2CDB','#00FF66','#FFFFFF'];
  let y = height/2;
  let spacing = width / (colors.length + 1);
  for (let i = 0; i < colors.length; i++) {
    fill(colors[i]);
    noStroke();
    ellipse((i+1)*spacing, y, 80, 80);
    if (colors[i] === currentColor) {
      stroke(255); strokeWeight(3);
      noFill();
      ellipse((i+1)*spacing, y, 100, 100);
    }
  }
}

function touchStarted() {
  let colors = ['#FF0066','#FFCC00','#00FFFF','#7B2CDB','#00FF66','#FFFFFF'];
  let spacing = width / (colors.length + 1);
  let y = height/2;
  for (let i = 0; i < colors.length; i++) {
    let dx = touches[0].x - (i+1)*spacing;
    let dy = touches[0].y - y;
    if (dx*dx + dy*dy < 40*40) {
      currentColor = colors[i];
      socket.emit('message', { type: 'color', hex: currentColor });
      redraw();
      return false;
    }
  }


  let t = touches[0];
  socket.emit('message', { type: 'touch', x: t.x, y: t.y });
  socket.emit('message', { type: 'yellowShift' });
  return false;
}

function touchMoved() {
  if (touches.length > 0) {
    let t = touches[0];
    socket.emit('message', { type: 'touch', x: t.x, y: t.y });
  }
  return false;
}
````
**microbit**  
````js
from microbit import *
import music
import utime

uart.init(baudrate=115200)
display.show(Image.HEART)

while True:
    if button_a.is_pressed():
        uart.write('A') 
        display.show(Image.PACMAN)
        utime.sleep_ms(400)
        display.show(Image.HEART)

    if button_b.is_pressed():
        uart.write('B')  
        display.show(Image.DIAMOND)
        utime.sleep_ms(400)
        display.show(Image.HEART)

    x = accelerometer.get_x()
    uart.write('X' + str(x) + '\n')  
    utime.sleep_ms(200)
````
**Nota**  
Me pondría 4, porque aunque el código no funcionó completamente como esperaba, sí logré desarrollar toda la actividad 1. Seguí todos los pasos, hice las pruebas y traté de que las visuales reaccionaran al ritmo de la canción. Considero que el esfuerzo y la intención de cumplir con la idea principal se reflejan en el trabajo.


