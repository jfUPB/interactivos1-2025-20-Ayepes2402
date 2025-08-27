# Unidad 3


## 🤔 Fase: Reflect

### Actividad 08

**Describe con tus palabras qué es una máquina de estados. ¿Cuáles son sus cuatro componentes fundamentales que has utilizado en esta unidad?**

Una máquina de estados es una manera de organizar un programa para que sepa qué hacer según la situación en la que esté. Tiene cuatro partes principales:  
* **Estados:** los diferentes momentos o modos en los que puede estar el programa.  
* **Eventos:** cosas que pasan y pueden hacer que cambie de estado, como presionar un botón.  
* **Transiciones:** el cambio de un estado a otro cuando ocurre un evento.  
* **Acciones:** lo que hace el programa en cada estado o cuando cambia de estado.  


**Explica por qué la técnica de máquina de estados es tan útil para gestionar la “concurrencia” (atender varios eventos y tareas “al mismo tiempo”) en un dispositivo con un solo hilo de ejecución como el micro:bit o en p5.js. ¿Qué problema soluciona en comparación con usar funciones como sleep()?**  
La máquina de estados ayuda a que un programa en micro:bit o p5.js pueda atender varias cosas a la vez sin bloquearse. Guarda el estado actual y en cada ciclo revisa qué hacer según los eventos. Esto es mejor que usar sleep(), porque sleep() detiene el programa y no deja responder a otras tareas, mientras que la máquina de estados avanza en pasos cortos y sigue reaccionando rápido.

**Imagina que tienes que añadir una nueva funcionalidad a la bomba: si se recibe un evento especial (por ejemplo, una combinación de botones o un comando serial) mientras la cuenta regresiva está activa, el tiempo se reduce a la mitad. ¿Cómo modificarías tu diagrama de máquina de estados para incluir este nuevo evento y acción?**  
Para agregar esta nueva función en la máquina de estados, modificaría el estado ARMED para que, si se recibe un evento especial, el tiempo de la cuenta regresiva se reduzca a la mitad. Este evento solo se podrá usar una vez por activación, así que pondría una condición que lo controle. No cambiaría los estados, solo agregaría esta nueva acción dentro del estado ARMED.

**Explica qué es un “vector de prueba” y por qué es una herramienta crucial para verificar que una máquina de estados funciona como se espera.**   
Un vector de prueba es como una lista de ejemplos donde ponemos qué pasa y qué debería hacer la máquina de estados en cada caso. Es importante porque así comprobamos si funciona bien y si responde como se espera, ayudando a encontrar fallos antes de usarla de verdad.
Parte 2: reflexión sobre tu proceso (Metacognición)

**¿Qué parte del diseño de la bomba te resultó más desafiante: crear el diagrama de estados o traducir ese diagrama a código? ¿Por qué?**  
Traducir ese diagrama al código porque, tal como dije en la unidad pasada, la parte de programar siempre se me ha dificultado.

**Describe un error o “bug” que encontraste al implementar tu programa. ¿Cómo te ayudó pensar en términos de estados, eventos y transiciones a identificar y solucionar el problema?**  
Un error que tuve fue que la bomba no pasaba al estado de explosión cuando el tiempo llegaba a cero. Pensar en estados, eventos y transiciones me ayudó a darme cuenta de que no había puesto bien el evento de “tiempo terminado” para que cambiara de estado. Cuando lo corregí, la bomba ya explotaba en el momento correcto.

**El problema de la bomba era complejo. ¿Qué estrategia usaste para abordarlo? ¿Comenzaste con una versión simple y añadiste funcionalidades poco a poco?**   
Decidí ir con una versión simple y fui añadiendo funcionalidades poco a poco para que no se me hiciera tan complejo al realizarlo.

**Ahora que entiendes el patrón de máquina de estados, ¿En qué otro tipo de proyecto o sistema de entretenimiento digital crees que podrías aplicarlo?**  
Se podría usar en un videojuego simple, donde hay estados como menú, jugando, pausa y fin. La máquina de estados ayuda a organizar qué hace el juego en cada momento y facilita agregar funciones sin complicar el programa.

### Actividad 09  

**¿Qué actividad, explicación o ejemplo de esta unidad te ayudó más a entender el poder de las máquinas de estados? ¿Qué elemento consideras que es indispensable y debería mantener?**  
Yo diría que las primeras actividades en conjunto me ayudaron a comprender mejor los temas, y me parece indispensable hacer ejemplos antes de realizar las actividades del apply.

**¿Hubo algún paso o actividad que te pareció confuso? ¿Qué cambiarías o eliminarías?**   
El código, porque es un problema mío, pero la verdad no cambiaría nada.

**¿Qué te habría ayudado a entender mejor?**   
La verdad no se me ocurre algo en estos momentos porque siento que se trató de explicar todo super bien.

**En una escala del 1 (muy fácil) al 5 (muy difícil), ¿Cómo calificarías la dificultad de pasar del análisis de un programa a diseñar y programar uno complejo? ¿Por qué?**   
3, porque las primeras actividades y la unidad pasada me ayudaron un poco más con los conceptos.

**¿Hay algo más que te gustaría compartir sobre tu proceso de aprendizaje en esta unidad? ¿Algún momento de frustración o de “¡Aha!” que quieras destacar?**  
Me gustaría destacar que mejoré un poco más en los conceptos y en la programación.


