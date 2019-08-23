
# Clase 2 | Repaso (continuación) 

La clase pasada revisamos *loops*. Repasamos el comportamiento del *loop for*. 

## Loops

### `while()`

Controla una secuencia de repeticiones. La estructura `while()` ejecuta continuamente una serie de declaraciones mientras que la evaluación de la expresión se mantiene en cierto. 

```java	
while (expression) {
  statements
}
```

La expresión puede ser "peligrosa" debido a que el código dentro del *loop while* no terminará hasta que la expresión dentro de *while* se convierta en falsa.

Ejemplo: 

```java
int i = 0;
while (i < 80) {
  line(30, i, 80, i);
  i = i + 5;
}
```

## Color

Hasta el momento hemos dibujado formas en blanco y negro y el fondo de la ventana se ha mantenido en gris claro. 

Para cambiar esto vamos a utilizar las funciones `background()` `fill` y `stroke`. 

Los valores de los parámetros tienen el rango de 0 a 255, donde 255 es blanco, 128 es un gris medio y 0 es negro. 

El siguiente ejemplo muestra tres diferentes valores en circulos que están sobre un fondo negro. 

```java
size(480, 120);
background(0); // negro
fill(204); // gris claro
ellipse(132, 82, 200, 200); // círculo gris claro
fill(153); // gris medio 
ellipse(228, -16, 200, 200); // círculo gris medio
fill(102); // gris oscuro
ellipse(268, 118, 200, 200); círculo gris oscuro
```

Es posible deshabilitar el contorno y el relleno con `noStroke()` y `noFill()`. 

```java
size(480, 120);
fill(153);
ellipse(132, 82, 200, 200);
noFill();
ellipse(228, -16, 200, 200);
noStroke();
ellipse(268, 118, 200, 200);
```

Si queremos usar valores más allá de la escala de grises, podemos usar tres parámetros para especificar los componentes de un color (rojo, verde y azu). 

```java
size(480, 120);
noStroke();
background(0, 26, 51);
fill(255, 0, 0);
ellipse(132, 82, 200, 200);
fill(0, 255, 0);
ellipse(228, -16, 200, 200);
fill(0, 0, 255);
ellipse(268, 118, 200, 200);
```

La definición de un color con la convención RGB proviene de la manera en que la computadora define colores en la pantalla. 

Los valores RGB se pueden definir en un rango que va de 0 a 255. 

Hay un cuarto valor que se puede utilizar para definir un valor de color. El valor alpha define transparencia. 

Este valor, como los que hemos visto hasta el momento, puede ir de 0 a 255 donde 0 define un color completalmente transparente y 255 un color completamente opaco. 

```java
size(480, 120);
noStroke();
background(204, 226, 225);
fill(255, 0, 0, 160);
ellipse(132, 82, 200, 200);
fill(0, 255, 0, 160);
ellipse(228, -16, 200, 200); 
27fill(0, 0, 255, 160);
ellipse(268, 118, 200, 200);
```
Otras formas de definir el color. 

## Aleatoriedad

Las computadoras pueden generar valores y comportamientos líneales muy facilmente. Sin embargo, el mundo físico se comporta de maneras diversas, muchas veces alejadas de ese comportamiento lineal. 

Es posible simular comportamientos y cualidad inpredecibles al generar números aleatorios. 

En Processing, una función que puede realizar esto es la función `random()` 

Antes de dibujar...

```java
void draw() {
float r = random(0, mouseX);
println(r);
}
```

El ejemplo anterior imprime valores aleatorios en la Consola, en un rango que está limitado por la posición del mouse en el eje X. 

La función `random()` siempre devuelve un valor de punto flotante. Hay que asegurarse que la variable declarada sea un número de punto flotante. Esto se puede determinar con `float`

El siguiente ejemplo usa los valores que genera `random()` para cambiar la posición de las líneas en la pantalla. Si el mouse se encuentra a la izquierda de la pantalla, el cambio es pequeño, si se mueve a la derecha, el valor se incrementa y el cambio es más notorio. 

```java
void setup() {
size(240, 120);
}
void draw() {
background(204);
for (int x = 20; x < width; x += 20) {
float mx = mouseX / 10;
float offsetA = random(-mx, mx);
float offsetB = random(-mx, mx);
line(x + offsetA, 20, x - offsetB, 100);
}
}
```

Si generamos valores alteatorios para mover objetos, la imagen resultante puede ser, aparentemente, más "natural". En el siguiente ejemplo, la posición del círculo se modifica por valores aleatorios en cada vuelta del `draw`. Debido a que el `background` no está declarado ni se actualiza en `draw()`, las posiciones anteriores permanecen dibujadas. 

```java
float speed = 2.5;
int diameter = 20;
float x;
float y;
void setup() {
size(240, 120);
x = width/2;
y = height/2;
}
void draw() {
x += random(-speed, speed);
y += random(-speed, speed);
ellipse(x, y, diameter, diameter);
}
```

## Transformaciones 

### translate(), rotate() y scale()

La función translate sirve para cambiar el sistema de coordenadas, por default (0, 0) a una localización diferente. 


```java
void setup() {
size(120, 120);
}
void draw() {
translate(mouseX, mouseY);
rect(0, 0, 30, 30);
}
```

Para el caso del ejemplo anterior, el sistema de coordenadas cambia de (0, 0) a la posición del mouse. cada vez que draw() dibuja algo, rect() se dibuja en el nuevo origen

La función rotate() rota el sistema de coordenadas. Tiene un solo parámetro, que es el ángulo (en radianes) de rotación. Su rotación es relativa a (0, 0), es decir, rota alrrededor del origen. 

```java
void setup() {
size(120, 120);
}
void draw() {
rotate(mouseX / 100.0);
rect(40, 30, 160, 20);
}
```

La transformación `scale()` cambia el tamaño de la figura seleccionada. 



```java
void setup() {
size(120, 120);
}

void draw() {
translate(mouseX, mouseY);
scale(mouseX / 60.0);
rect(-15, -15, 30, 30);
}
```


### `pushMatrix() y popMatrix()`

Para aislar los efectos de una transformación de forma tal que no afecten a otros comandos, usamos las funciones `pushMatrix()` y `popMatrix()`

Cuando `pushMatrix()` está corriendo, salva una copia del sistema de coordenadas que está en ejecución y reanuda ese sistema después de `popMatrix()`; 

Esto es útil cuando requerimos hacer transformaciones para una figura, pero no queremos que tenga consecuencias para otras. 

```java
void setup() {
size(120, 120);
}
void draw() {
pushMatrix();
translate(mouseX, mouseY);
rect(0, 0, 30, 30);
popMatrix();
translate(35, 10);
rect(0, 0, 15, 15);
}
```

Para rotar una figura en su propio eje: 

```java
void setup() {
size(120, 120);
}
void draw() {
rotate(mouseX / 100.0);
rect(40, 30, 160, 20);
}
```

## Otras funciones 

### mouseX y mouseY 

## Ejercicios para la próxima clase. 


## Referencias 

[Processing Reference](https://processing.org/reference/)

- Reas, C., & Fry, B. (2014). Processing: a programming handbook for visual designers and artists. Massachusetts: MIT Press.

- Reas, C., McWilliams, C., & LUST. (2010). Form + Code: in design, art and architecture. New York:Princeton Architectural Press.
