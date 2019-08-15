
# Clase 1 | Repaso

Presentación.

Fechas, recursos e información -> [https://github.com/EmilioOcelotl/centro20-I_CC3/README.md](https://github.com/EmilioOcelotl/centro20-I_CC3/README.md)

[Type and Form sculpture](https://devart.withgoogle.com/#/catalogued/6682104213536768)

Algunas ideas introductorias se pueden encontrar en -> [https://github.com/EmilioOcelotl/centro20-I_CC2/tree/master/centro2_190816/README.md](https://github.com/EmilioOcelotl/centro20-I_CC2/tree/master/centro2_190816)

## Evaluación del grupo

Ejecución de Processing, PDE, proyectos anteriores. 

## Funciones (en processing)

Las funciones son los los bloques basicos para construir programas en Processing. 

Algunas de ellas son size() line() fill() 

El poder de las funciones está en la modularidad. Son unidades de software independientes que pueden ser usadas para construir programas más complejos. 

Más adelante el curso aprenderemos a escribir funciones para extender las capacidades de Processing más allá de sus características incorporadas. 

## Condicionales

Las condicionales funcionan de manera parecida a las preguntas. Permiten a un programa realizar una acción si la respuesta a la pregunta es "cierto" o realizar otra acción si la respuesta es "falso". 

Las preguntas formuladas dentro de un programa son siempre declaraciones lógicas o relacionales. 

Por ejemplo, si la variable 'i' es igual a cero, dibuja una línea.

```java
size(640, 360);
background(0);

for(int i = 10; i < width; i += 10) {
  // If 'i' divides by 20 with no remainder draw 
  // the first line, else draw the second line
  if((i % 20) == 0) {
    stroke(255);
    line(i, 80, i, height/2);
  } else {
    stroke(153);
    line(i, 20, i, 180); 
  }
}
```
## Loops

Por default, Processing *loopea* continuamente el código escrito en `draw()`. Sin embargo, el *loop* `draw()` puede detenerse cuando escribimos `noLoop()`. En ese caso, el loop `draw()` puede reanudarse con `loop()`; 

Ejemplo: 

```java 
void setup() {
  size(200, 200);
  noLoop();  // draw() will not loop
}

float x = 0;

void draw() {
  background(204);
  x = x + .1;
  if (x > width) {
    x = 0;
  }
  line(x, 0, x, height); 
}

void mousePressed() {
  loop();  // Holding down the mouse activates looping
}

void mouseReleased() {
  noLoop();  // Releasing the mouse stops looping draw()
}
``` 
Otra estructura de código llamada `for()` hace posible correr una de código más de una vez. Esto permite condensar una repetición en pocas líneas. 

El siguiente ejemplo dibuja un patrón 

```java
size(480, 120);
strokeWeight(8);
line(20, 40, 80, 80);
line(80, 40, 140, 80);
line(140, 40, 200, 80);
line(200, 40, 260, 80);
line(260, 40, 320, 80);
line(320, 40, 380, 80);
line(380, 40, 440, 80);
```

Que puede simplificarse de la siguiente manera: 

```java
size(480, 120);
strokeWeight(8);
for (int i = 20; i < 400; i += 60) {
line(i, 40, i + 60, 80);
}
```

Las llaves, es decir { y }, distinguen a `for()` (también a `while()`). El código que se encuentra entre llaves se llama bloque. Este es el código que va a ser repetido en cada iteración del *loop* `for()`. 

Dentro de los paréntesis hay tres declaraciones separadas por punto y coma. De izquierda a derecha, estas declaraciones son: *init, test* y *update*

```java
for (init; test; update) {
statements
}
```

En *init* fijamos el valor inicial, muchas veces declarando una variable que usaremos dentro del loop for. El nombre de variable `i` 

## Color

## Aleatoriedad

## Transformaciones (pushMatrix(), popMatrix(), rotate())
