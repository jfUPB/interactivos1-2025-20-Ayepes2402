
# Evidencias de la unidad 5

### Autoevaluacion    
**CRITERIOS	NOTA	JUSTIFICACIÓN**   
| CRITERIOS | NOTA | JUSTIFICACIÓN|
|----------|----------|----------|
| 1. Profundidad de la Indagación  |  5   | Mientras hacía el trabajo, iba preguntando a mi compañero o investigaba por mi propia cuenta para así comprender mejor los temas.  |
| 2. Calidad de la Experimentación |  5   | Mientras realizaba las actividades, siempre las ponía a prueba con el micro:bit y dejaba evidencia en la bitácora con fotos. |
| 3. Análisis y Reflexión |  4.6   | En la bitácora hay fotos de los procedimientos y algunos textos breves indicando si algo no se podía leer en una opción u otra.  |
| 4. Apropiación y Articulación de Conceptos |  4.5  | La bitácora muestra comprensión de los temas, pero siento que aún me falta mejorar un poco.    |
| TOTAL| 4.78 |    |   

### Actividad 05   
**En la unidad anterior abordaste la construcción de un protocolo ASCII. En esta unidad realizaste lo propio con un protocolo binario. Realiza una tabla donde compares, según la aplicación que modificaste en la fase de aplicación de ambas unidades, los siguientes aspectos: eficiencia, velocidad, facilidad, usos de recursos. Justifica con ejemplos concretos tomados de las aplicaciones modificadas.**   

| Aspecto             | Protocolo ASCII                                                            | Protocolo Binario                                                      |
| ------------------- | -------------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| **Eficiencia**      | Menor eficiencia, ya que cada número se envía como caracteres (más bytes). | Mayor eficiencia: los datos se envían directamente en formato binario. |
| **Velocidad**       | Más lento debido a la cantidad de datos transmitidos.                      | Más rápido, transmite menos bytes por la misma cantidad de datos.      |
| **Facilidad**       | Más fácil de interpretar y depurar (legible para humanos).                 | Más difícil de leer directamente, necesita decodificación.             |
| **Uso de recursos** | Mayor uso de ancho de banda y procesamiento.                               | Menor uso de recursos, pero requiere mayor precisión en el manejo.     |

**¿Por qué fue necesario introducir framing en el protocolo binario?**  
Porque en el protocolo binario no hay comas ni saltos de línea que separen los datos. Si no se indica bien dónde empieza y termina cada paquete, el programa puede leer mal los datos. El framing ayuda a detectar el inicio de cada paquete con un byte especial, así el programa sabe que desde ahí empiezan los datos válidos.  

**¿Cómo funciona el framing? ¿Qué es un carácter de sincronización?**    
Funciona poniendo un byte especial al inicio para que el programa pueda encontrar el comienzo de cada paquete. Luego de eso, el programa sabe que vienen exactamente 8 bytes (o la cantidad que se haya definido) y puede leerlos correctamente.  

**¿Qué es el checksum y para qué sirve?**   
Es un byte especial que se usa para marcar el inicio de un paquete de datos.  

**En la función readSerialData() del programa en p5.js: ¿Qué hace la función concat? ¿Por qué?**    
```js
function readSerialData() {
    let available = port.availableBytes();
    if (available > 0) {
        let newData = port.readBytes(available);
        serialBuffer = serialBuffer.concat(newData);
    }
```
**¿Qué hace la función concat? ¿Por qué?**   
La función concat une los nuevos datos que llegan del puerto (newData) con los que ya estaban en el buffer (serialBuffer). Se usa para no perder datos cuando estos llegan por partes, y así guardar todo en orden hasta tener un paquete completo que pueda procesarse bien.  

**En la función readSerialData() tenemos un bucle que recorre el buffer solo si este tiene 8 o más bytes ¿Por qué?**  
Porque cada paquete tiene 8 bytes. Si hay menos, el paquete está incompleto y no se puede procesar aún.  

````js
while (serialBuffer.length >= 8) {
    if (serialBuffer[0] !== 0xaa) {
      serialBuffer.shift();
      continue;
    }
`````

**En el código anterior qué significa 0xaa?**  
Es el byte de sincronización, o sea, una marca especial que indica el inicio de un paquete válido.  

**En el código anterior qué hace la función shift y la instrucción continue? ¿Por qué?**  
Se usan para descartar datos basura antes del inicio del paquete. Si el primer byte no es 0xAA, se borra y se sigue buscando el comienzo real.

**Si hay menos de 8 bytes qué hace la instrucción break? ¿Por qué?**  
Detiene el bucle porque no hay suficientes datos para formar un paquete. Se espera a que lleguen más.  

````js
    if (serialBuffer.length < 8) break;
`````
**¿Cuál es la diferencia entre slice y splice? ¿Por qué se usa splice justo después de slice?**
* slice copia los datos.  
* splice los elimina del buffer original.  
Se usan juntos para leer el paquete y luego quitarlo del buffer, evitando procesarlo dos veces.

````js
let packet = serialBuffer.slice(0, 8);
serialBuffer.splice(0, 8);
`````

**A la siguiente parte del código se le conoce como programación funcional**   
````js
    let computedChecksum = dataBytes.reduce((acc, val) => acc + val, 0) % 256;
````

**¿Cómo opera la función reduce?**  
Suma todos los valores del arreglo dataBytes, y con % 256 lo deja en 1 byte.
Se usa para calcular el checksum y verificar que los datos estén bien.  

**¿Por qué se compara el checksum enviado con el calculado? ¿Para qué sirve esto?**
````js
if (computedChecksum !== receivedChecksum) {
    console.log("Checksum error in packet");
    continue;
}
````
Para saber si el paquete llegó sin errores. Si no coinciden, el paquete se considera dañado y se ignora.  

**En el código anterior qué hace la instrucción continue? ¿Por qué?**
Salta al siguiente ciclo del bucle. Se usa para ignorar el paquete con error y seguir leyendo los siguientes.  

¿Qué es un DataView? ¿Para qué se usa?  
Es una herramienta para leer datos binarios en distintos formatos, como int16 o uint8.
Sirve para interpretar los bytes como números reales (por ejemplo, coordenadas o botones).  

````js
let buffer = new Uint8Array(dataBytes).buffer;
let view = new DataView(buffer);
````
**¿Por qué es necesario hacer estas conversiones y no simplemente se toman tal cual los datos del buffer?**   
Porque los datos en el buffer solo son números del 0 al 255 (bytes), pero no dicen por sí solos qué significan.
Si no los convertimos con funciones como getInt16() o getUint8(), estaríamos leyendo mal los datos. Las conversiones permiten entender los bytes según el formato original en que fueron enviados, y así el programa puede funcionar correctamente.  
````js
    microBitX = view.getInt16(0) + windowWidth / 2;
    microBitY = view.getInt16(2) + windowHeight / 2;
    microBitAState = view.getUint8(4) === 1;
    microBitBState = view.getUint8(5) === 1;
````

