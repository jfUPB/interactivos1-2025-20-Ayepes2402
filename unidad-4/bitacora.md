# Evidencias de la unidad 4

## Código

[Enlace a la aplicación a modificar](https://editor.p5js.org/generative-design/sketches/P_2_1_2_04)

Código a modificar:

``` js
// P_2_1_2_04
//
// Generative Gestaltung – Creative Coding im Web
// ISBN: 978-3-87439-902-9, First Edition, Hermann Schmidt, Mainz, 2018
// Benedikt Groß, Hartmut Bohnacker, Julia Laub, Claudius Lazzeroni
// with contributions by Joey Lee and Niels Poldervaart
// Copyright 2018
//
// http://www.generative-gestaltung.de
//
// Licensed under the Apache License, Version 2.0 (the "License");
// you may not use this file except in compliance with the License.
// You may obtain a copy of the License at http://www.apache.org/licenses/LICENSE-2.0
// Unless required by applicable law or agreed to in writing, software
// distributed under the License is distributed on an "AS IS" BASIS,
// WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
// See the License for the specific language governing permissions and
// limitations under the License.

/**
 * moving corners of rectangles in a grid
 *
 * MOUSE
 * position x          : corner position offset x
 * position y          : corner position offset y
 * left click          : random position
 *
 * KEYS
 * s                   : save png
 */
'use strict';

var tileCount = 20;
var actRandomSeed = 0;

var rectSize = 30;

function setup() {
  createCanvas(600, 600);
  colorMode(HSB, 360, 100, 100, 100);
  noStroke();
  fill(192, 100, 64, 60);
}

function draw() {
  clear();

  randomSeed(actRandomSeed);

  for (var gridY = 0; gridY < tileCount; gridY++) {
    for (var gridX = 0; gridX < tileCount; gridX++) {

      var posX = width / tileCount * gridX;
      var posY = height / tileCount * gridY;

      var shiftX1 = mouseX / 20 * random(-1, 1);
      var shiftY1 = mouseY / 20 * random(-1, 1);
      var shiftX2 = mouseX / 20 * random(-1, 1);
      var shiftY2 = mouseY / 20 * random(-1, 1);
      var shiftX3 = mouseX / 20 * random(-1, 1);
      var shiftY3 = mouseY / 20 * random(-1, 1);
      var shiftX4 = mouseX / 20 * random(-1, 1);
      var shiftY4 = mouseY / 20 * random(-1, 1);

      push();
      translate(posX, posY);
      beginShape();
      vertex(shiftX1, shiftY1);
      vertex(rectSize + shiftX2, shiftY2);
      vertex(rectSize + shiftX3, rectSize + shiftY3);
      vertex(shiftX4, rectSize + shiftY4);
      endShape();
      pop();
    }
  }
}

function mousePressed() {
  actRandomSeed = random(100000);
}

function keyReleased() {
  if (key == 's' || key == 'S') saveCanvas(gd.timestamp(), 'png');
}

```

[Enlace a la aplicación modificada](https://editor.p5js.org/Ayepes2402/sketches/xg1sXloFe)

Código modificado:

``` js
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <title>P_2_1_2_04 + micro:bit (Azul)</title>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.6.0/p5.min.js"></script>
</head>
<body>
  <button id="connect">Conectar micro:bit</button>
  <script>

    let tileCount = 20;
    let actRandomSeed = 0;
    let rectSize = 30;

    let xOffset = 0;
    let yOffset = 0;

    let lastA = 0;
    let lastB = 0;

    let port;

    async function connectMicrobit() {
      try {
        port = await navigator.serial.requestPort();
        await port.open({ baudRate: 115200 });
        readLoop();
      } catch (err) {
        console.error("Error conectando micro:bit:", err);
      }
    }

    async function readLoop() {
      const textDecoder = new TextDecoder();
      const reader = port.readable.getReader();
      let buffer = "";

      try {
        while (true) {
          const { value, done } = await reader.read();
          if (done) break;
          if (value) {
            buffer += textDecoder.decode(value, { stream: true });
            let lines = buffer.split("\n");
            buffer = lines.pop();

            for (let line of lines) {
              let parts = line.trim().split(",");
              if (parts.length === 4) {
                let x = parseInt(parts[0]);
                let y = parseInt(parts[1]);
                let a = parseInt(parts[2]);
                let b = parseInt(parts[3]);

                xOffset = map(x, -1024, 1024, 0, width);
                yOffset = map(y, -1024, 1024, 0, height);

                if (a === 1 && lastA === 0) {
                  actRandomSeed = int(random(100000));
                }

                if (b === 1 && lastB === 0) {
                  saveCanvas("miPatron", "png");
                }

                lastA = a;
                lastB = b;
              }
            }
          }
        }
      } catch (err) {
        console.error("Error en readLoop:", err);
      } finally {
        reader.releaseLock();
      }
    }

    document.getElementById("connect").addEventListener("click", connectMicrobit);

    // p5.js

    function setup() {
      createCanvas(600, 600);
      colorMode(HSB, 360, 100, 100, 100);
      noStroke();
      fill(192, 100, 64, 60);
    }

    function draw() {
      clear();

      randomSeed(actRandomSeed);

      for (let gridY = 0; gridY < tileCount; gridY++) {
        for (let gridX = 0; gridX < tileCount; gridX++) {
          let posX = width / tileCount * gridX;
          let posY = height / tileCount * gridY;

          let shiftX1 = xOffset / 20 * random(-1, 1);
          let shiftY1 = yOffset / 20 * random(-1, 1);
          let shiftX2 = xOffset / 20 * random(-1, 1);
          let shiftY2 = yOffset / 20 * random(-1, 1);
          let shiftX3 = xOffset / 20 * random(-1, 1);
          let shiftY3 = yOffset / 20 * random(-1, 1);
          let shiftX4 = xOffset / 20 * random(-1, 1);
          let shiftY4 = yOffset / 20 * random(-1, 1);

          push();
          translate(posX, posY);
          beginShape();
          vertex(shiftX1, shiftY1);
          vertex(rectSize + shiftX2, shiftY2);
          vertex(rectSize + shiftX3, rectSize + shiftY3);
          vertex(shiftX4, rectSize + shiftY4);
          endShape(CLOSE);
          pop();
        }
      }
    }
  </script>
</body>
</html>
```

## Video

[Video demostratativo](https://youtu.be/yEYheHYkGno?si=YEhnBH1eGDOLxMc2)




