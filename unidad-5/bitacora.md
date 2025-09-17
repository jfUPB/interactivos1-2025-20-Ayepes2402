
# Evidencias de la unidad 5

### Actividad 01  
**Describe cómo se están comunicando el micro:bit y el sketch de p5.js. ¿Qué datos envía el micro:bit?**    
El micro:bit se conecta al computador por el puerto serial (USB) y envía datos en texto plano a 115200 baudios. Cada 0,1 s manda las lecturas del acelerómetro en X y Y, junto con el estado de los botones A y B.

**¿Cómo es la estructura del protocolo ASCII usado?**  
El mensaje es una sola línea de texto ASCII con cuatro valores separados por comas y terminado en salto de línea \n. El orden es: x, y, aState, bState.

**Muestra y explica la parte del código de p5.js donde lee los datos del micro:bit y los transforma en coordenadas de la pantalla.**  
```js
let data = port.readUntil("\n");
let values = data.trim().split(",");
microBitX = int(values[0]) + windowWidth / 2;
microBitY = int(values[1]) + windowHeight / 2;
microBitAState = values[2].toLowerCase() === "true";
microBitBState = values[3].toLowerCase() === "true";
```  
Ese fragmento lee la línea de texto que envía el micro:bit, la separa por comas y convierte los dos primeros datos en números para las coordenadas X y Y, ajustándolos al centro de la ventana. Los dos últimos los pasa a valores lógicos para saber si los botones A y B están presionados. Así transforma el mensaje del micro:bit en posiciones de dibujo y estados de botones para el sketch.

**¿Cómo se generan los eventos A pressed y B released que se generan en p5.js a partir de los datos que envía el micro:bit?**  
* Si newAState pasa de false a true sucede el evento A pressed, que crea un nuevo tamaño de línea y guarda la posición del clic.  
* Si newBState pasa de true a false sucede B released, que cambia el color del trazo.  

**Capturas de pantalla de los algunos dibujos que hayas hecho con el sketch.**
<img width="1538" height="1592" alt="20250912_143056" src="https://github.com/user-attachments/assets/0fb68822-9f54-4662-8479-2d717d4e0204" />  

### Actividad 2  
<img width="557" height="188" alt="image" src="https://github.com/user-attachments/assets/808af6e2-59ad-4d45-bfef-fc6185c7f01f" />    

**Captura el resultado del experimento anterior. ¿Por qué se ve este resultado?**  
Porque muestra el estado del newAState y va cambiando el resultado de la pantalla si se unde el boton A o B  

**Ahora cambia la opción de Mostrar datos como a Todo en Hex y vuelve a capturar el resultado.**  
<img width="776" height="197" alt="image" src="https://github.com/user-attachments/assets/494ed8a1-29f5-45b4-b902-75f76975aeb7" />  
**¿Cómo está relacionado con esta línea de código?**  
Debido a que de esta manera se pueden ver los 8 bites que se están usando. 

**Lo que ves ¿Cómo está relacionado con esta línea de código?**  
```js 
data = struct.pack('>2h2B', xValue, yValue, int(aState), int(bState))
```  
porque en el programa aparecen grupos de seis bytes que son justo los paquetes que estoy enviando con esa linea de código  

**No te parece que el resultado es un poco más difícil de leer que el texto en ASCII?**  
si, porque en el anterior se entendía más porque usaba true y false haciendo más fácil el entendimiento de lo que está sucediendo.

**¿Qué ventajas y desventajas ves en usar un formato binario en lugar de texto en ASCII?**  
El formato binario es más rápido y ocupa menos espacio porque manda los números tal cual, sin convertirlos a texto. En cambio el ASCII es fácil de entender y revisar, aunque usa más memoria y es más lento.

**Ahora te voy a proponer un experimento que te permitirá ver mejor los datos. Cambia el código del micro:bit por este:**  
```js
# Imports go at the top
from microbit import *
import struct
uart.init(115200)
display.set_pixel(0,0,9)

while True:
    if accelerometer.was_gesture('shake'):
        xValue = accelerometer.get_x()
        yValue = accelerometer.get_y()
        aState = button_a.is_pressed()
        bState = button_b.is_pressed()
        data = struct.pack('>2h2B', xValue, yValue, int(aState), int(bState))
        uart.write(data)
````
**Captura el resultado del experimento**
<img width="760" height="196" alt="image" src="https://github.com/user-attachments/assets/1a518170-d83e-4781-b37a-88a7ea6e7fbd" />  
**como en este no se puede ver toca ponerlo en todo hex para que se pueda leer**
<img width="794" height="190" alt="image" src="https://github.com/user-attachments/assets/17cb87a2-0a0f-40eb-a233-2b3ae3afe4fc" />  

**¿Cuántos bytes se están enviando por mensaje? ¿Cómo se relaciona esto con el formato '>2h2B'? ¿Qué significa cada uno de los bytes que se envían?**   
Se envían 6 bytes por mensaje. El formato '>2h2B' indica que se transmiten dos valores de 2 bytes (x e y del acelerómetro) y dos de 1 byte (estado de los botones A y B). Cada byte representa una parte específica de esos datos.

**Recuerda de la unidad anterior que es posible enviar números positivos y negativos para los valores de xValue y yValue. ¿Cómo se verían esos números en el formato '>2h2B'?**  
En el formato '>2h2B', los valores positivos y negativos de xValue y yValue se codifican como enteros de 2 bytes usando complemento a dos. Por ejemplo, 300 sería 01 2C y -300 sería FE D4.  

**Ahora realiza el siguiente experimento para comparar el envío de datos en ASCII y en binario.**
```js
# Imports go at the top
from microbit import *
import struct
uart.init(115200)
display.set_pixel(0,0,9)

while True:
    if accelerometer.was_gesture('shake'):
        xValue = accelerometer.get_x()
        yValue = accelerometer.get_y()
        aState = button_a.is_pressed()
        bState = button_b.is_pressed()
        data = struct.pack('>2h2B', xValue, yValue, int(aState), int(bState))
        uart.write(data)
        uart.write("ASCII:\n")
        data = "{},{},{},{}\n".format(xValue, yValue, aState,bState)
        uart.write(data)
```
**Captura el resultado del experimento.**   
<img width="1054" height="230" alt="image" src="https://github.com/user-attachments/assets/75d717dd-c3d3-45ec-9a9a-d4516df57975" />  
<img width="1000" height="225" alt="image" src="https://github.com/user-attachments/assets/a97a44e8-fe74-4bf0-9e05-9da4aa99101b" />  

**¿Qué diferencias ves entre los datos en ASCII y en binario? ¿Qué ventajas y desventajas ves en usar un formato binario en lugar de texto en ASCII? ¿Qué ventajas y desventajas ves en usar un formato ASCII en lugar de binario?**  
Los datos en formato binario son más compactos y rápidos de transmitir, pero difíciles de leer sin herramientas especiales. En cambio, los datos en ASCII son fáciles de entender y depurar, aunque ocupan más espacio y son más lentos de enviar. Por eso, el binario es mejor para eficiencia y el ASCII para claridad.  

### Actividad 03  




