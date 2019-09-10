
# Clase 5 | Práctica de programación orientada a objetos

## Ejemplos relevantes de código creativo

## Processing

En esta clase realizaremos un ejercicio parecido al de la clase pasada. 

Agregaremos algunas funcionalidades, por ejemplo, determinar con variables el tamaño del arreglo de círculos y el límite del tamaño de los círculos. 

Posteriormente sustituiremos los cículos por textos provenientes de un texto con saltos de línea y relativamente complejo. 

Aprenderemos cómo leer y manipular arreglos de strings, para eso, tendremos que repasar cómo se comportan los arreglos

Finalmente introduciremos algunas ideas sobre las clases en el contexto de la programación orientada a objetos y los constructores. 

De esta manera, trataremos de delimitar el control sobre el ejemplo que vamos utilizando. 

### Arreglos (repaso) 

### Relación con la clase String

¿Es posible sustituir la posición de los círculos con texto dibujado en pantalla, leído de un archivo txt?

Los siguientes ejemplos que aparecen en el documento de la clase pasada pueden ayudarnos a resolver este problema. 

```java
String[] lines = loadStrings("ohplaces.txt");
for (int i = 0; i < lines.length; i++) {
println(lines[i]);
}
```

split

```java
String s = "a, b";
String[] p = split(s, ", ");
println(p[0]); 
println(p[1]);
```

```java
int paso = 2;

void setup(){
size(600, 600);
// background(0);
String[] lines = loadStrings("ohplaces.txt");

}

void draw(){
  background(0);
  paso = paso + 1;
  //fill(paso);
textSize((paso % 30)+1);

// println(lines[int(random(100))]); 

rectMode(CENTER); // interpreta posX posY como el centro de la figura

text(lines[int(random(100))], width/2, height/2, 80, 80);
text(lines[int(random(100))], width/4, height/4, 80, 80);
text(lines[int(random(100))], width/4*3, height/4*3, 80, 80);

}
```

### Estructura y sintaxis de una clase

Hasta el momento hemos abordado tres nociones: objeto, método y atributo. 

Vamos a agregar un concepto más: clase

Una clase define un grupo de métodos (funciones) y campos/atributos. Si bien podría parecer que un objeto y una clase son similares, tienen diferencias. 

Estas diferencias tienen que ver con la manera en la que se estructuran comportamientos y atributos en la POO. 

Importante: Un objeto es una instancia simple de una clase. 

Entonces, podemos complejizar el ejercicio de la analogía entre objeto, método y atributo.

Por ejemplo clase radio, con el atributo radio frecuencia y el método asignar frecuencia. 

Una instancia de esa clase, es decir un objeto, podría ser radio FM (87.5 -108 Mhz) y radio de onda corta (3 -30 Mhz) 

Otro atributo podría ser el color de la radio, no solamente la radio frecuencia


### Ejemplo de cómo se usa una clase y ejercicio de hacer una clase


Cuando definimos una clase creamos nuestro propio tipo de tipos de datos. 

Ya hemos visto que existen tipos de formas de almacenar datos en Processing como: int, float y boolean. 

La clase pasada hablamos un poco de objetos y revisamos String, una clase para empezar a trabajar con series de caracteres. 

Definir una clase es parecido a este último tipo de datos: es posible almacenar variables y métodos dentro de un mismo nombre. 

Para crear una clase primero debemos tener claro que queremos que haga el código. 

En este sentido es común que primero hagamos la lista de variables que requeriremos (estos serán los campos o atributos). 

Tener en cuenta las variables que utilizaremos nos ayudará a darnos cuenta de qué tipo serán. 

El nombre de una clase es importante: Los nombres de las clases siguen las mismas convenciones que las variables (¿Cuáles?). 

Sin embargo, los nombres de las clases siempre deben ir en mayúsculas. 

Ya hemos visto un poco de esto con String, esto ayuda a que podamos distinguir a partes del código como String o PImage de los tipos de funciones que se escriben con minúsculas como int o boolean. 

Podemos elegir, por ejemplo el nombre circulo. 

Si consideramos que el ejemplo que hicimos a lo largo de la clase es una función ellipse() entonces los parámetros/campos de nuestra clase pueden seguir la misma lógica

float x - coordenadas del círculo en x

float y - coordenadas del círculo en y

float diameter - diametro del círculo

Una vez que los atributos y el nombre de la clase han sido determinados, hay que considerar cómo el programa se comportará sin el uso de un objeto. 

Para el caso del ejemplo que hemos utilizado, algunos parámetros están definidos en variables, básicamente posición del círculo y diámetro. 

Entonces, traduzcamos el programa que hicimos a la forma de estructurar el código que hemos mencionado hasta el momento

¿Qué pasa? 

Es importante señalar varias cosas: 

La primera es que la clase Circulo no es muy útil hasta el momento, sin embargo es el inicio para ver de qué manera podemos introducir lo que hasta el momento hemos visto. 

Es importante señalar que la clase Circulo y el objeto cir son cosas diferentes. 

Los objetos son creados a partir de una clase y una clase describe un conjunto de campos/atributos y métodos. 

Una instancia de una clase funciona como una variable y como cualquier variable, debe tener un nombre único. 

Si queremos realizar varias instancias de clase, podemos diferenciarlas entre ellas por medio de la declaración de distintos nombres. 

En la próxima clase complejizaremos y trabajaremos en torno a otras cosas, por ejemplo, constructores. 

### Constructores


### Ejercicio en clase /  tarea

Tomar el ejemplo que hasta el momento hemos construido, variar formas, tamaños, colores y comportamientos. Enviarlos por email con comentarios que expliquen cómo funciona. 
