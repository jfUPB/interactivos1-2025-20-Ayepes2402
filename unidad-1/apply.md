# Unidad 1

## 🛠 Fase: Apply

## Actividad 6

# Escribe el enlace a tu programa en el editor de p5.js.

https://editor.p5js.org/alejogonzdav41/sketches/aJg-BAAgc

# Copia el código de tu programa en la bitácora (recuerda insertarlo usando markdown y el lenguaje javascript).
```
  let port;
  let connectBtn;
  let connectionInitialized = false;
x=200

  function setup() {
    createCanvas(400, 400);
    background(220);
    port = createSerial();
    connectBtn = createButton("Connect to micro:bit");
    connectBtn.position(80, 300);
    connectBtn.mousePressed(connectBtnClick);
  }

  function draw() {
    background(220);
    circle(x,200,50)

    if (port.opened() && !connectionInitialized) {
      port.clear();
      connectionInitialized = true;
    }

    if (port.availableBytes() > 0) {
      let dataRx = port.read(1);
      if (dataRx == "A") {
        x-=5
      } else if (dataRx == "B") {
        x+=5
      }
    }


    if (!port.opened()) {
      connectBtn.html("Connect to micro:bit");
    } else {
      connectBtn.html("Disconnect");
    }
  }

  function connectBtnClick() {
    if (!port.opened()) {
      port.open("MicroPython", 115200);
      connectionInitialized = false;
    } else {
      port.close();
    }
  }
```
# Copia el código del micro:bit en la bitácora (recuerda insertarlo usando markdown y el lenguaje python).
```
from microbit import *

uart.init(baudrate=115200)

while True:
      if button_a.was_pressed():
          uart.write('A')
          uart.write('B')
```
