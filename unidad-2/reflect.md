# Unidad 2


## 🤔 Fase: Reflect

### Actividad 06

**Parte 1: recuperación de conocimiento (Retrieval Practice)**  

**Describe con tus palabras qué es una máquina de estados. ¿Cuáles son sus cuatro componentes fundamentales que has utilizado en esta unidad?**  
Una máquina de estados es como un esquema que usamos para entender y organizar cómo funciona algo según la situación en la que esté.  

* **Estados:** Son las diferentes formas o situaciones en las que puede estar el sistema    
* **Eventos:** Son las cosas que suceden y que pueden provocar que el sistema cambie de estado  
* **Acciones:** Son las tareas que realiza el sistema cuando ocurre un evento o cuando entra o sale de un estado   

**Explica por qué la técnica de máquina de estados es tan útil para gestionar la “concurrencia” (atender un temporizador y botones “al mismo tiempo”) en un dispositivo con un solo hilo de ejecución como el micro:bit. ¿Qué problema soluciona en comparación con usar funciones como sleep()?**  

La máquina de estados sirve mucho en el micro:bit porque ayuda a manejar varias cosas al mismo tiempo, como un temporizador y botones, sin que el programa se quede trabado. Si se usa sleep() el micro:bit se “duerme” y no hace nada más hasta que pase el tiempo, pero con la máquina de estados el programa va revisando todo el rato en qué estado está y si pasa algo, así puede reaccionar rápido. Esto permite que, aunque esté esperando que pase el tiempo para cambiar de estado, también pueda detectar si se presionó un botón u ocurrió otra cosa.

**Imagina que tienes que añadir una nueva funcionalidad a la bomba temporizada: si se agita (shake) el micro:bit mientras la cuenta regresiva está activa, el tiempo se reduce a la mitad. ¿Cómo modificarías tu diagrama de máquina de estados para incluir este nuevo evento y acción?**  

Añadiría un estado adicional que parta del estado Cuenta regresiva. Se llegaría a este estado cuando el micro:bit detecte que fue agitado, y la acción que realizaría sería reducir el tiempo que queda a la mitad. Luego, desde este nuevo estado, el temporizador continuaría su cuenta normal hasta que llegue a cero o ocurra algún otro evento que detenga la bomba.  

**Explica qué es un “vector de prueba” y por qué es una herramienta crucial para verificar que una máquina de estados funciona como se espera.**  

Un vector de prueba es una lista de casos que indican el estado inicial, el evento y el resultado esperado, y sirve para comprobar que una máquina de estados reacciona correctamente en cada situación y así detectar errores antes de usarla.  

**Parte 2: reflexión sobre tu proceso (Metacognición)**  

**¿Qué parte del diseño de la bomba temporizada te resultó más desafiante: crear el diagrama de estados (Actividad 04) o traducir ese diagrama a código MicroPython (Actividad 05)? ¿Por qué?**

Para mi la parte más dificil del trabajo de la bomba fue programar porque nunca fui muy buena en ello y siempre se me complica.

**Describe un error o “bug” que encontraste al implementar tu programa. ¿Cómo te ayudó pensar en términos de estados, eventos y transiciones a identificar y solucionar el problema?**

Pensar en términos de estados, eventos y transiciones me ayudó a entender mejor el flujo del programa, ver con claridad qué debía pasar en cada situación y organizar el código de forma que fuera más fácil encontrar y corregir errores.

**El problema de la bomba era complejo. ¿Qué estrategia usaste para abordarlo? ¿Comenzaste con una versión simple y añadiste funcionalidades poco a poco?**

Fui poco a poco añadiendo los componentes en el programa para asi hacerlo mas organizado y entender mejor.

**Ahora que entiendes el patrón de máquina de estados, ¿En qué otro tipo de proyecto o sistema de entretenimiento digital crees que podrías aplicarlo?**

Se podria usar en videojuegos para manejar los diferentes modos de un personaje (afk, caminando, saltando o atacando) y las acciones que hace según las teclas que se presionen. 

### Actividad 07
**Encuentra a un compañero de trabajo.  
Intercambien las URLs de sus bitácoras de aprendizaje.  
Revisa con atención las entradas de tu compañero para las Actividades 04 (diagrama de la bomba) y 05 (código y pruebas).  
Analiza de manera crítica el diseño y la implementación de tu compañero y deja un comentario de retroalimentación específico y constructivo.**

El mapa es bastante simple pero me parece que cumple bien con lo que se pidió en la actividad, lo que me pareció más curioso es que tuvimos problemas para entener la logica del mapa pero yo tuve más a la hora de programar.

### Actividad 08

**¿Qué actividad, explicación o ejemplo de esta unidad te ayudó más a entender el poder de las máquinas de estados? ¿Qué elemento consideras que es indispensable y debería mantener?**

La actividad de las caritas felices ya que me pareció simple de entender y cumplía la función de ayudar a entender los conceptos para la actividad, lo que considero indispensable es primero hacer ejemplos en grupo para luego nosotros intentar hacerlos.

**¿Hubo algún paso o actividad que te pareció confuso, innecesariamente complicado o que aportó poco a tu aprendizaje? ¿Qué cambiarías o eliminarías?**

La actividad que me pareció mas confusa fue la de la bomba pero fue mas que todo po9rque me pareció un tema un poco dificil para mi pero no cambiaría nada, diría que es algo más de mis habilidades que de la actividad.

**¿Qué te habría ayudado a entender mejor?**

Poner un poco más de atención porque hubo una clase en la que andaba muy cansada y eso me afectó un poco a la hora de haacer las actividades.

**En una escala del 1 (muy fácil) al 5 (muy difícil), ¿Cómo calificarías la dificultad de pasar del análisis de un programa (Actividad 03) al diseño desde cero de uno complejo (Actividad 04 y 05)? ¿Por qué?**

4 porque era un reto bastante complejo para mi y grande.

**¿Hay algo más que te gustaría compartir sobre tu proceso de aprendizaje en esta unidad? ¿Algún momento de frustración o de “¡Aha!” que quieras destacar?**

Quisiera compartir que esta unidad mi proceso fue complejo pero hice lo que pude para salir adelante en las actividades.



