
# Clase 1 | Repaso

Presentación.

Fechas, recursos e información -> [https://github.com/EmilioOcelotl/centro20-I_CC3](https://github.com/EmilioOcelotl/centro20-I_CC3)

¿Cómo funciona este documento? 

[Type and Form sculpture](https://devart.withgoogle.com/#/catalogued/6682104213536768)

## Ejemplos de proyectos creativos cuyo fundamento es la programación

Seguimiento de hashtags. Ejercicios que las personas suben a las redes. No necesariamente son los grandes artistas. 

[Zack Lieberman](https://www.instagram.com/zach.lieberman/)

[Algorave 100 fragments - Atsushi Tadoroko](https://vimeo.com/286688569)

[Circulo & Meio - Renick Bell & Joana Chicau](https://www.youtube.com/watch?v=bFqYRpUbKqs)

[Hydra Patterns](https://twitter.com/hydra_patterns)

## Evaluación

Introducción breve -> [https://github.com/EmilioOcelotl/centro20-I_CC2/blob/master/centro2_190816/README.md](https://github.com/EmilioOcelotl/centro20-I_CC2/blob/master/centro2_190816)

Ejecución de Processing, PDE, sketches. 

Variables, coloreado del código y componentes de un sketch de Processing.

## Funciones (en processing)

Las funciones son los los bloques basicos para construir programas en Processing. 

Algunas de ellas son *size()* *line()* *fill()* 

La modularidad es una de las características más importantes de las funciones en Processing. Son unidades de software independientes que pueden ser usadas para construir programas más complejos. 

Más adelante aprenderemos a escribir funciones para extender las capacidades de Processing más allá de sus características incorporadas. 

Imprimir en la consola. 

### Sistema de coordenadas

Recordemos que la pantalla de una computadora es una cuadrícula de elementos que emiten luz llamados pixeles.

Escribimos las coordenadas de un pixel de la siguiente manera: (x, y)

Si invocamos una pantalla de 200x200 pixeles, la esquina superior izquierda es el origen, o sea (0, 0) y la esquina inferior derecha es (199, 199)

¿En este ejemplo, qué coordenadas tendría el centro? 

### Formas

Mientras tanto, recordemos las formas básicas 

`line(x1, y1, x2, y2)`

Ejemplo: 

```java
size(480, 120);
line(20, 50, 420, 110);
```

Rectángulos...

`rect(x, y, anchura, altura)`

```java
// Dibujar un rectángulo con punto inicial en (180, 60), ancho de 220 y alto de 40
size(480, 120);
rect(180, 60, 220, 40);
```
Círculos...

`ellipse(x, y, width height)` 

```java
size(480, 120);
ellipse(278, -100, 400, 400);
```

Otras formas son: `triangle, quad` y `arc.` 

El sistema de coordenadas inicia arriba y a la izquierda ¿Por qué?

El orden de las instrucciones importa, en este ejemplo el rectángulo se dibuja encima del círculo debido a que aparece después en el código.

```java
size(480, 120);
ellipse(140, 0, 190, 190);
rect(160, 30, 260, 20);
```

En este otro, la elipse se encuentra encima debido a que aparece después 

```java
size(480, 120);
rect(160, 30, 260, 20);
ellipse(140, 0, 190, 190);
```

### `setup()` y `draw()`

Processing puede correr continuamente para dibujar o para interactuar en el tiempo. Para realizar esto, Processing tiene la función *draw()*. 

El código que se encuentra en *draw()* corre de arriba a abajo y se repite hasta que detienes el programa. Cada "vuelta" del *draw()* es un *frame*. 

Por *default* Processing corre a 60 fotogramas por segundo, esto quiere decir que hay 60 ciclos por segundo dentro del *draw()* 

```java
void draw() {
println("I'm drawing");
println(frameCount);
}
```

Processing también tiene una función llamada *setup()* que corre una vez que el programa inicia. 

## Condicionales

Las condicionales funcionan de manera parecida a las preguntas. Permiten a un programa realizar una acción si la respuesta a la pregunta es "cierto" o realizar otra acción si la respuesta es "falso". 

Las preguntas formuladas dentro de un programa son siempre declaraciones lógicas o relacionales. 

Por ejemplo, si la variable 'i' es igual a cero, dibuja una línea.

```java
void setup() {
size(240, 120);
strokeWeight(30);
}
void draw() {
background(204);
stroke(102);
line(40, 0, 70, height);
if (mousePressed) {
stroke(0);
} else {
stroke(255);
}
line(0, 70, width, 50);
}
```
## Loops

### `loop()` y `noLoop()`

Como ya vimos, Processing *loopea* continuamente el código escrito en `draw()`. Sin embargo, el *loop* `draw()` puede detenerse cuando escribimos `noLoop()`. En ese caso, el loop `draw()` puede reanudarse con `loop()`; 

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

### `for()`

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

Las llaves, es decir { y }, distinguen a `for()`. El código que se encuentra entre llaves se llama bloque. Este es el código que va a ser repetido en cada iteración del *loop* `for()`. 

Dentro de los paréntesis hay tres declaraciones separadas por punto y coma. De izquierda a derecha, estas declaraciones son: *init, test* y *update*

```java
for (init; test; update) {
statements
}
```
En *init* fijamos el valor inicial, muchas veces declarando una variable que usaremos dentro del loop for. 

El nombre de variable `i` es frecuentemente usado, pero no hay nada especial en él. 

*Test* evalúa el valor de esta variable (para el caso del primer código, revisa si `i` sigue siendo menor que 400). *Update* cambia el valor de la variable, agregando 60 antes de repetir el *loop*.

Un diagrama puede clarificar el flujo de un *for loop* 

Cabe destacar que la declaración *text* es siempre una expresión relacional que compara dos valores con un operador relacional. En el ejemplo de arriba, la expresión es "i < 400" y el operador es < (menor que). Los operadores relacionales más comunes son: 

| Símbolo | Operación        |
|:-------:|:----------------:|
| >       | Mayor que        | 
| <       | Menor que        |
| >=      | Mayor o igual que|
| <=      | Menor que        |
| ==      | Igual a          |
| !=      | No es igual a    |

El resultado de la evaluación siempre es cierto o falso. 


## Referencias 

[Processing Reference](https://processing.org/reference/)

- Reas, C., & Fry, B. (2014). Processing: a programming handbook for visual designers and artists. Massachusetts: MIT Press.

- Reas, C., McWilliams, C., & LUST. (2010). Form + Code: in design, art and architecture. New York:Princeton Architectural Press.

