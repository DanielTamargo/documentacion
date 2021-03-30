## ¿Qué es JavaScript?

> JavaScript (abreviado comúnmente JS) es un lenguaje de programación interpretado, dialecto del estándar ECMAScript. Se define como orientado a objetos, basado en prototipos, imperativo, débilmente tipado y dinámico.  
> Se utiliza principalmente del lado del cliente, implementado como parte de un navegador web permitiendo mejoras en la interfaz de usuario y páginas web dinámicas3​ y JavaScript del lado del servidor (Server-side JavaScript o SSJS). Su uso en aplicaciones externas a la web, por ejemplo en documentos PDF, aplicaciones de escritorio (mayoritariamente widgets) es también significativo.

## Cómo probar el código HTML + JS (+ CSS, etc)

Tendremos diferentes formas de probar el código:  

<br>

1- Arrastrar el archivo HTML al explorador para que este lo ejecute (o escribir la ruta completa en el buscador del navegador).

<br>

2- Lanzar un servidor local y hacer pruebas en este, utilizando por ejemplo **XAMPP**
> XAMPP es una distribución de Apache completamente gratuita y fácil de instalar que contiene MariaDB, PHP y Perl. El paquete de instalación de XAMPP ha sido diseñado para ser increíblemente fácil de instalar y usar.

Si instalamos y utilizamos XAMPP, sólo tendremos que iniciar el servicio Apache y acceder a la dirección localhost:puerto, por defecto el puerto configurado para este servicio es el 80 por lo que simplemente accediendo a la dirección localhost ya estaremos en la dirección del servidor.

Todos los archivos que queramos ver en dicha dirección tendrán que estar dentro de la carpeta 'htdocs' ubicada en la ruta donde hayamos instalado XAMPP (ruta por defecto en Windows 10: C:\xampp\htdocs)
[Descargar XAMPP aquí.](https://www.apachefriends.org/es/download.html)

<br>

3- Utilizar la herramienta [Visual Studio Code](https://code.visualstudio.com) para desarrollar todos los ejemplos y ejercicios.

Además, existe la extensión **Live Reload** que ofrece el propio VSCode la cual, utilizando un puerto (por defecto el 5500), abrirá el documento HTML que deseemos y cada vez que un cambio sea guardado, la página se refrescará automáticamente y se podrá ver el efecto de dicho cambio.


<br>

**Importante:** Todos los mensajes que queramos mostrar por consola utilizando por ejemplo console.log(), si queremos verlos en la página tendremos que hacer clic derecho -> inspeccionar (o Ctrl + Mayus + i), y acceder a la pestaña Console, ahí se mostrarán todos los mensajes.

----
## Ejecutar código JavaScript desde un documento HTML  

Si queremos incorporar nuestro código JS al archivo html podremos hacerlo de diferentes formas:  

<br>

1- Creando directamente un script con el propio código
```html
<script type="text/javascript">
  alert('Hola Mundo!');
</script>
```  

2- Generando directamente el código en los propios eventos
```html
<button onclick="alert('¡Hola Mundo!')">Saludar</button>
```

3- Haciendo referencia a un archivo local
```html
<script type="text/javascript" src="./codigo.js"></script>
```  

4- Haciendo referencia a un script online
```html
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
```  

Atributos que podemos añadir a la etiqueta script:
- Cuando queremos hacer una petición de un recurso y tenemos que señalar si la petición es anónima o con credenciales: [**crossorigin**](https://www.w3schools.com/tags/att_script_crossorigin.asp)
- Cárgarlo **después** de cargar la página: [**defer**](https://www.w3schools.com/tags/att_script_defer.asp)
- Cargarlo **mientras** se carga la página: [**async**](https://www.w3schools.com/tags/att_script_async.asp)

<br>

Personalmente considero que lo mejor es tener el código bien planteado y ordenado, disponiendo diferentes archivos .js para las diferentes funciones y utilidades necesarias y hacer referencia a ellos desde el documento HTML cuando sea necesario.

----
## ¿Y si el navegador no puede ejecutar código JavaScript?

Añadir código JavaScript a una página web es maravilloso, pero puede ser utilizado con fines ruines. Por esto mismo ciertos clientes desactivan la opción de ejecutar código JavaScript en sus navegadores.
No es algo habitual ni mucho menos, se trata de un ínfimo número de casos, por ejemplo los ordenadores de instituciones gubernamentales lo desactivan con el fin de proteger los datos.

Si queremos contemplar la posibilidad de que navegadores con JavaScript desasctivado accedan a nuestra página, podremos utilizar la etiquieta <noscript> para notificarles un mensaje o contenido personalizado.
Ejemplo:
```html
<noscript>
    <h2>Hola!</h2>
    <p>No tienes activado JavaScript, por lo que es posible que la página no cargue
    o funcione correctamente.</p>
</noscript>
```

----
## Miscelánea

Ciertas cosas que pueden ser útiles o que viene bien conocer 
- undefined = sin definir
- null = sin valor, nulo
- NaN = Not a Number (por ejemplo al hacer 5 * "dani")
- prompt("Hola"); = muestra una alerta con un input para guardarlo
- document.write(variable); = escribe en el documento directamente

----
## Variables

### Tipos de variables y su scope (amplitud o rango donde podrán ser utilizadas)

[Hay 3 formas de declarar una variable:](https://www.w3schools.com/js/js_variables.asp)
**let**: declarará una variable que sólo existirá en el bloque donde se haya declarado.
**var**: declarará una variable global (por defecto las variables son tipo var).
**const**: declarará una variable global y constante.
```javascript
const letra = 'a';
var numero = 1;
var numero = 2; // Se sobreescribe sin problemas

if (true) {
    console.log(letra); // a
    console.log(numero); // 2
    
    let resultado = numero + 3;
    console.log(resultado); // 5
}

console.log(letra); // a
console.log(numero); // 2
console.log(resultado); // error: ReferenceError: resultado is not defined

letra = 'b'; // error: TypeError: Assignment to constant variable
```  
Como nota, puedes crear una variable let que se llame igual que una variable var y al hacer referencia a dicho nombre priorizará la variable let, pero no es recomendable, hay que centrarse en hacer un código limpio y **claro**, es decir, fácil de entender, y repetir nombres de variables solo complica las cosas.

----
## Use Strict

Si queremos que sea obligatorio utilizar la indicación **var**, **let** o **const** para declarar una variable dando uso a las buenas prácticas de programación, tendremos que añadir **'use strict';** al principio del archivo .js (en la primera línea).
```javascript
'use strict'; // En la primera línea del código!
```
También podremos añadir 'use strict'; particularmente a una función
```javascript
function funcionEstricta() {
    'use strict'; // En la primera línea de la función!
    var saludo = "hola!"
}
```

Si no utilizamos use strict, podremos crear una variable directamente dándole nombre y valor y JS sobreentenderá que estamos creando dicha variable tipo var con dicho valor.
En cambio, si utilizamos use strict, JS no nos mimará tanto, por lo que tendremos que ir declarando y concretando cada variable.
Parece que es dar un paso atrás, pero realmente ayuda a la hora de crear un código correcto.

Es muy fácil colarse y equivocarse al escribir el nombre de una variable y teclear dos letras al revés, o acostumbrarse a crear variables sin indicar que son var, haciendo difícil entender de dónde ha salido y en qué momento hemos necesitado o declarado dicha variable.
Use strict nos obligará a utilizar "las buenas prácticas" a la hora de programar, haciendo que nuestro código quede más claro y ordenado.

---
## Buenas prácticas de programación

En el punto anterior hemos mencionado el término 'Buenas prácticas de programación' y quizás sea la primera vez que lo escuchas.
Las buenas prácticas de programación son un conjunto de reglas (pueden ser opcionales u obligatorias) que se adoptan a la hora de programar con el fin de mejorar la calidad del software, facilitar el proceso de desarrollo para el programador, facilitar la legibilidad y mantebilidad del código fuente, evitar ciertos errores comunes, etc.
Las reglas más importantes son:
- El largo máximo de cada línea (líneas eternas resultan en líneas ilegibles).
- Convenciones de nombres para las variables.
- Tabulaciones en el código dentro de las estructuras de control y funciones.
- Utiliza sólo una instrucción por línea.
- Utiliza un espacio después de las comas.
- Y otros.

Las buenas prácticas no solo competen al lenguaje de programación JavaScript, sino a todos ellos puesto que sus beneficios son más que válidos.

[Aquí tenemos un pdf que explica en profundidad y con ejemplos las buenas prácticas de programación en C.](http://zeus.inf.ucv.cl/~ifigueroa/lib/exe/fetch.php/teaching/buenaspracticasc.pdf)

----
## Estructuras de control

### If... else if... else
```javascript
if (condicion) {
    alert('primera condición verdadera!!');
} else if (condicion2) {
    alert('segunda condición verdadera!');
} else {
    alert('ninguna de las condiciones era verdadera :(');
}
```  

### Switch
```javascript
switch (accion) {
    case 'saludar': // Si accion == 'saludar', ejecutamos el código
        alert('hola!');
        break; // Si no añadimos el break, ejecutaría el siguiente case
    case 'despedir':
        alert('adiós!');
        break;
    default:
        alert('acción no contemplada!')
}
```  

### For (fori)
```javascript
for (var i = 0; i < 10; i++) {
   console.log(`¡Hola! Valor de i: ${i}`);
}
```  

### While
```javascript
var n = 0;
while (n < 7) {
    n++;
    console.log(`¡Hola! Te he saludado ${n} veces`);
}
```  

### Do While

Funciona igual que el while, pero siempre se ejecutará al menos una vez
```javascript
var n = 0;
do {
    n++;
    console.log(`¡Hola! Te he saludado ${n} veces`);
} while (n < 7);
```  

### For ... in

Podemos utilizarlo de dos formas diferentes:  

1- Recorrer las propiedades de un objeto
```javascript
var objeto = {
    nombre: "Daniel",
    edad: 25
};
for (propiedad in objeto) {
    console.log(propiedad); // Nombre de la propiedad
    console.log(objeto[propiedad]) // Valor de dicha propiedad del objeto
}
```  
__Nota:__ podríamos utilizar objeto.hasOwnProperty(propiedad) para comprobar si en efecto un objeto tiene dicha propiedad.

2- Recorrer las posiciones de un array
```javascript
var lista_personas = [ "Daniel", "María", "Irune", "Aitor" ];
for (posicion in lista_personas) {
    console.log(posicion); // Posición que está recorriendo
    console.log(lista_personas[posicion]); // Valor de dicha posición en el array
}
```  

### For ... of

En el For...in estábamos recorriendo y obteniendo las posiciones de un array o el nombre de las propiedades de un objeto. 
Ahora, con el For...of vamos a recorrer directamente los valores.
```javascript
var lista_personas = [ "Daniel", "María", "Irune", "Aitor" ];
for (persona of lista_personas) {
    console.log(persona); // output: Valor -> ejemplo: Daniel
}
```  

### Try ... catch ... finaly

```javascript
try {
    // Dentro del try ejecutamos el código que puede lanzar un error o excepción
    abrirFichero(); 
} catch(ex) {
    // En el catch trataremos la excepción
    console.log(`Error: ${ex}`); 
} finally {
    // En el bloque finally escribiremos el código que se ejecutará siempre
    cerrarFichero();
}
```  

----
## Operadores aritméticos

| Operador | Descripción    | Ejemplo    |
|----------|----------------|------------|
| +        | Suma           | 2 + 3 = 5  |
| -        | Resta          | 2 - 2 = 0  |
| /        | División       | 2 / 2 = 1  |
| *        | Multiplicación | 2 * 2 = 4  |
| %        | Resto          | 3 % 2 = 1  |
| ++       | Incremento     | 2++ = 3    |
| --       | Decremento     | 2-- = 1    |
| **       | Exponente      | 2 ** 3 = 8 |

----
## Operadores de comparación

| Operador | Descripción               | Ejemplo            |
|----------|---------------------------|--------------------|
| ==       | Igual                     | '2' == 2 es true   |
| !=       | No es igual               | '2' != 2 es false  |
| ===      | Estrictamente igual       | '2' === 2 es false |
| !==      | No es estrictamente igual | '2' !== 2 es true  |
| >        | Mayor que                 | 2 > 2 es false     |
| >=       | Mayor o igual que         | 2 >= 2 es true     |
| <        | Menor que                 | 2 < 2 es false     |
| <=       | Menor o igual que         | 2 <= 2 es true     |

Nota: == y != cotejan los valores independientemente del tipo de variable. En cambio === y !== cotejan que tanto el valor como el tipo de variable sean iguales (es decir, estrictamente iguales).

----
## Operadores de asignación

| Operador | Descripción                  | Ejemplo abreviado | Ejemplo sin abreviar |
|----------|------------------------------|-------------------|----------------------|
| =        | Asignación                   | x = y             | x = y                |
| +=       | Asignación de adición        | x += y            | x = x + y            |
| -=       | Asignación de resta          | x -= y            | x = x - y            |
| *=       | Asignación de multiplicación | x *= y            | x = x * y            |
| /=       | Asignación de división       | x /= y            | x = x / y            |

[Existen muchos más operadores de asignación. Puedes consultarlos haciendo clic aquí.](https://developer.mozilla.org/es/docs/Web/JavaScript/Guide/Expressions_and_Operators#operadores_de_asignaci%C3%B3n)

----
## Funciones

**Función sin valor de retorno**
```javascript
function prueba1() {
    console.log('ejecutando la función!');
}

prueba1();
``` 

**Función con valor de retorno**
```javascript
function prueba2() {
    return 'resultado de la función!';
}

var resultado = prueba2();
console.log(resultado);
``` 

**Función con parámetros**
```javascript
function prueba3(var1, var2) {
    return var1 + var2;
}

console.log(prueba3(2, 2)); // 4
``` 

**Función con parámetros opcionales**
```javascript
function prueba4(var1, var2, var3 = 0) {
    return var1 + var2 + var3;
}

console.log(prueba4(2, 2)); // 4
console.log(prueba4(2, 2, 8)); // 12
``` 

**Función con parámetro REST**
```javascript
function prueba5(var1, var2, ...var3) {
    console.log(var1) // Mostrará el valor de la variable 1
    console.log(var2) // Mostrará el valor de la variable 2
    
    // Mostrará un array con todas las demás variables que haya añadido
    //  si no hay añadido ninguna, mostrará un array vacío: []
    console.log(var3) 
}

prueba5(2, 4);
``` 

Notas:
- Una función puede llamar a otra.
- Si tenemos un trozo de código repetido a lo largo de nuestro desarrollo, deberemos refactorizarlo en una función la cual llamaremos desde donde deseemos.
- Un parámetro REST no tiene nada que ver con las API REST, son cosas distintas. Simplemente JavaScript entenderá que cuando introducimos un parámetro REST debe introducir todas las variables "extra" que reciba en un array el cual podremos manejar.
- Si creas variables dentro de una función, aunque sean tipo var, no podrás llamarlas desde fuera de la función. Porque esa variable sólo va a existir y vivir dentro de la función, si quieres acceder al valor tendrás que devolverla con un return y recogerla cuando llames a dicha función.

----
## Callbacks

Un **callback** (llamada de vuelta) es una función que recibe como argumento otra función y la ejecuta.

```javascript
var x = 2;
var y = 4;

function resultado(var1, var2, funcion) {
    return funcion(var1, var2);
}

// Podemos guardar una función en una variable
var sumar = function (n1, n2) {
    return n1 + n2;
}
// Y pasarle esa función de la misma manera
var res = resultado(x, y, sumar);
console.log(res); // 6

// También podemos pasarle la función construyéndola a la par que se la pasamos
var res = resultado(x, y, function(n1, n2) {
    return n1 * n2;
});
console.log(res); // 8
``` 

Utilidades de utilizar Callbacks:
- Poder controlar pasar una función como parámetro a otra función (como en el ejemplo).
- Controlar la ejecución asíncrona con callbacks.
- Callbacks para eliminar el conocimiento en las dependencias.

[Puedes ver en profundidad todos los usos de los Callbacks con explicaciones y ejemplos aquí.](https://link.medium.com/UriUqvfvJeb)

----
## Funciones flecha

```javascript
var x = 2;
var y = 4;

function resultado(var1, var2, funcion) {
    return funcion(var1, var2);
}

// Función flecha
var sumar = (num1, num2) => {
    return x + y;
}

console.log(resultado(x, y, sumar)); // 6
``` 

Nota: si la función flecha recibe solo un parámetro no harán falta los paréntesis.

----
## Arrays

> Un array es un tipo de dato estructurado que permite almacenar un conjunto de datos. Se puede considerar una lista donde almacenas valores y objetos. En muchos lenguajes los arrays deben almacenar un conjunto de datos homogéneo, es decir, todos los datos deberán ser del mismo tipo, pero en JavaScript no es el caso, podremos guardar diferentes tipos de datos en un mismo array.

Aprendamos cómo trabajar con los arrays.
### Crear un array
```javascript
var nombres = ["Dani", "Aitor", "Irune"];
console.log(nombres); // ["Dani", "Aitor", "Irune"]

// Un array puede contener distintos tipos de datos
var datos = [true, 4, "Vitoria", null];
console.log(datos); // [true, 4, "Vitoria", null]
```  

### Obtener los valores de un array
```javascript
var nombres = ["Dani", "Aitor", "Irune"];

// La primera posición será la posición 0
// index 0 -> Dani
// index 1 -> Aitor
// index 2 -> Irune
// index 3 -> Sin definir (no hay un cuarto valor)

var primerNombre = nombres[0]; 
var aitor = nombres[1];
var tercerNombre = nombres[2];
var cuartoNombre = nombres[3];

console.log(primerNombre); // Dani
console.log(aitor); // Aitor
console.log(tercerNombre); // Irune
console.log(cuartoNombre); // undefined
```

### Añadir un valor a un array
```javascript
// Añadir un valor al final de un array
//     Forma 1- método push() (recomendado)
var nombres = ["Dani", "Aitor", "Irune"];
nombres.push("María");
console.log(nombres); // ["Dani", "Aitor", "Irune", "María"]

//     Forma 2- utilizar .length
var nombres = ["Dani", "Aitor", "Irune"];
nombres[nombres.length] = "Juan"
console.log(nombres); // ["Dani", "Aitor", "Irune", "Juan"];

// Añadir un valor a una posición fija de un array
var nombres = ["Dani", "Aitor", "Irune"];
nombres[1] = "Carla";
console.log(nombres); // ["Dani", "Carla", "Irune"]

nombres[3] = "Alex";
console.log(nombres); // ["Dani", "Carla", "Irune", "Alex"]

// Si añadimos un valor a una posición dejando huecos en medio
var nombres = ["Dani"];
nombres[3] = "Ana";
console.log(nombres); // ["Dani", empty x2, "Ana"]
``` 

### Recorrer un array
```javascript
var nombres = ["Dani", "Aitor", "Irune"];

// Recorrer posiciones de un array
for (index in nombres) {
    console.log(index); // Posición
    console.log(nombres[index]); // Valor en dicha posición
}

// Otra forma de recorrer las posiciones de un array
for (let i = 0; i < nombres.length; i++) {
    console.log(i); // Posición
    console.log(nombres[i]); // Valor en dicha posición
}

// Recorrer directamente valores de un array (for each)
for (nombre of nombres) {
    console.log(nombre); // Valor
}
```

### Desestructurar un array
```javascript
var nombres = ["Dani", "Aitor", "Irune"];

// Otra forma de obtener los datos es desestructurar el array
var [uno, dos, tres, cuatro] = nombres;
console.log(uno); // Dani
console.log(dos); // Aitor
console.log(tres); // Irune
console.log(cuatro); // Undefined

// Podemos saltar un valor
var [dani, , irune] = nombres;
console.log(dani); // Dani
console.log(irune); // Irune

// Podemos guardar los valores sobrantes en otro array (parámetro REST)
var [primerNombre, ...otrosNombres] = nombres;
console.log(primerNombre); // Dani
console.log(otrosNombres); // ["Aitor", "Irune"]

// Al desestructurar podemos asignar valores por defecto
var [uno, dos, tres, cuatro="Sin nombre"] = nombres;
console.log(uno); // Dani
console.log(dos); // Aitor
console.log(tres); // Irune
console.log(cuatro); // Sin nombre
```
[Aprende todo sobre la desestructuración aquí.](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)

----
## DOM (Document Object Model)

> HTML es un lenguaje de etiquetado padre-hijo, es decir, existe una etiqueta general (padre) y dentro de esta etiqueta general se irán generando otras etiquetas (hijos) con los distintos elementos. Un hijo podrá tener otros hijos, etc.

Por ejemplo:

```html
<html>
    <head>
        <title>Test</title>
    </head>
    <body>
        <div class="contenedor">
            ...
        </div>
    </body>
</html>
```
Podemos ver que dentro de la etiqueta html, tenemos las etiquetas head y body, y dentro de estas tenemos otros elementos y así sucesivamente.  

A través del DOM podremos acceder a los diferentes elementos del HTML en nuestro código JavaScript.  

Una cosa a destacar será el uso de **camel case**, ¿qué significa esto? Supondrá el uso de una letra mayúscula al juntar dos palabras debido a no poder usar guiones en el nombre de los métodos. 
Por ejemplo, en css tenemos el método **text-decoration: underline** para definir que el texto estará subrayado, en cambio, en JavaScript al no poder utilizar ese guión en el nombre del método, utilizaremos camel case, quedando como **element.style.textDecoration = "underline"**. Podemos apreciar que en CSS es text-decoration mientras que en JavaScript será textDecoration, eso es camel case.

Para ello, tendremos que aprender las diferentes formas de hacer referencia a uno o varios elementos, y los métodos que existen para modificar su contenido, modificar sus propiedades, eliminarlo, crearlo, añadirle hijos, etc.
**Para poder utilizar el DOM correctamente tendremos que tener ciertos conocimientos mínimos de HTML (y de CSS si queremos modificar el estilo).**

Aquí veremos unos pocos ejemplos y una tabla con algunos de los métodos disponibles.  
Archivo **index.html**
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ejemplos DOM JavaScript</title>
    <script src="ejemplos.js" defer></script>
</head>
<body>
    <div id="div1"></div>
    <p class="parrafo1"></p>
    <p class="parrafo1"></p>
    <div id="padre">
        <p>Primer Hijo</p>
        <p>Segundo Hijo</p>
        <a>Último Hijo</a>
    </div>
</body>
</html>
```

Archivo **ejemplos.js**
```javascript
// Buscar un elemento por su id
var div1 = document.getElementById('div1');

div1.style.color = "darkred"; // Modificar el color de la fuente con nombre
div1.style.fontSize = "32px" // Modificar el tamaño de la fuente
div1.innerHTML = 'Hola Mundo!'; // Modificar su contenido visible

// Buscar varios elementos por su clase (se almacenan en un array)
var parrafos1 = document.getElementsByClassName('parrafo1');
console.log(parrafos1.length); // 2
parrafos1[0].style.color = "#222a";  // Color con código hexadecimal
parrafos1[0].style.textDecoration = "underline"; // Subrayar el texto
parrafos1[0].innerHTML = "Soy el primer párrafo de la clase parrafo1!";

var parrafo2 = parrafos1[1];
parrafo2.style.color = "rgb(10, 50, 200)"; // Color con código rgb
parrafo2.style.fontWeight = "bolder"; // Negrita
parrafo2.innerHTML = "Y yo soy el segundo!";

// Para obtener los elementos hijos de un elemento
var elementoPadre = document.getElementById('padre');
var primerHijo = elementoPadre.firstElementChild;
console.log(primerHijo); // <p>Primer Hijo</p>

// Obtener todos los hijos de un elemento
var hijos = document.getElementById('padre').children;
var segundoHijo = hijos[1];
console.log(segundoHijo); // <p>Segundo Hijo</p>

// Obtener el hermano de un elemento
var tercerHijo = segundoHijo.nextElementSibling;
console.log(tercerHijo); // <a>Último hijo</a>

// Crear elemento y añadirlo al final del body
var btn = document.createElement('BUTTON');
btn.innerText = '¡Apriétame!'; // Le añadimos texto al botón
btn.addEventListener('click', () => { alert('¡Hola Mundo!') }); // Evento onclick
document.body.appendChild(btn);

// Escribir texto directamente en el documento (al final del body)
document.write('¡Fin del ejemplo!');
```

Este ejemplo ha sido un ejemplo muuuy breve y simple, donde podemos observar cómo buscar un elemento por su ID, modificar su contenido y también cómo recoger en un array todos los elementos de una clase.

A continuación vamos a ver muchos de los métodos de uso habitual y que aunque no haya que memorizar, estaría bien conocer de su existencia.

### DOM: Buscar elementos
| Método                          | Descripción                                                                                                                                              |
|---------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| getElementById('id')            | Devuelve el elemento que tenga definido el ID a buscar.                                                                                                  |
| getElementsByClassName('class') | Devuelve un array HTMLCollection que contiene todos los elementos que tengan la clase especificada.                                                      |
| getElementsByTagName('tag')     | Devuelve un array HTMLCollection que contiene todos los elementos que tengan el tag especificado.                                                        |
| querySelector('#id')            | Si introducimos una almohadilla antes del dato, buscará y devolverá un elemento por su id.                                                               |
| querySelector('.class')         | Si introdoucimos un punto antes del dato, buscará y devolverá un elemento por su clase. En caso de haber varios, devolverá el primero  que encuentre. |
| querySelectorAll('.class')         | Si introdoucimos un punto antes del dato, buscará y devolverá todos los elementos de esa clase. Los devolverá en un array. |

[Todos los métodos y su documentación aquí.](https://www.w3schools.com/jsref/dom_obj_document.asp)

### DOM: Añadir, editar y eliminar atributos
| Método                        | Descripción                                                                                                                                              |
|-------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| setAttribute('type', 'value') | Crea el atributo y le asigna el valor. Si el atributo ya existía, reemplaza su valor.                                                                    |
| getAttribute('type')          | Devuelve el valor del atributo. Si el atributo no existe, devolverá null.                                                                                |
| removeAttribute('type')       | Elimina el atributo.                                                                                                                                     |

### DOM: Atributos útiles que puede tener cualquier nodo
| Atributo        | Descripción                                                                                                                                                                                                                             |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| class           | Lista de clases.                                                                                                                                                                                                                        |
| contentEditable | Recibirá true o false y definirá si el contenido es editable o no.                                                                                                                                                                      |
| dir             | Indica la dirección del texto. Por ejemplo: rtl indicará right to left.                                                                                                                                                                 |
| hidden          | Recibirá true o false y definirá si el nodo está oculto o no lo está.                                                                                                                                                                   |
| style           | Sirve para configurar el estilo del nodo (con css).                                                                                                                                                                                     |
| tabindex        | Indica si forma parte del tab, es decir, si al apretar la tecla tab, se seleccionará el nodo.  También, se respetará el orden, por lo que al hacer tab buscará el tabindex menor, luego, el siguiente tabindex, y así consecutivamente. |
| title           | Al poner el ratón encima del nodo mostrará el valor de este atributo, se usa generalmente para mostrar descripciones o detalles.                                                                                                        |

### DOM: Atributos de Inputs
| Atributo    | Descripción                                                                                                                               |
|-------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| value       | Devuelve el valor (también se puede usar para asignarle un valor).                                                                        |
| type        | Devuelve el tipo (también se puede usar para asignarle el tipo). Ejemplos: text, file, datetime-local...                                  |
| accept      | Si el atributo es tipo file, se puede configurar qué archivos aceptará únicamente. Ejemplo: accept='image/png'                            |
| form        | Se le puede asignar un formulario a un botón para que al presionarlo funcione como submit del mismo aún sin estar dentro del propio form. |
| minLength   | Define la cantidad mínima de caracteres necesarios.                                                                                       |
| maxLength   | Define la cantidad máxima de caracteres admitidos.                                                                                        |
| placeholder | Funciona como un hint, es decir, sirve para sugerir o indicar qué debería introducir.                                                     |
| required    | Su valor será true o false y definirá si el input es obligatorio o no.                                                                    |

### DOM: Configurar el atributo Style
Puedes configurarlo línea a línea a través de código JavaScript. Algunos ejemplos:
| Método                                      | Descripción                                                                           |
|---------------------------------------------|---------------------------------------------------------------------------------------|
| style.color = '#32b'               | Le asigna el color #32b al elemento.                                                  |
| style.padding = '30px'             | Asigna un padding de 30px alrededor del elemento.                                     |
| style.fontSize = '32px'            | Asigna un tamaño de fuente de 32px.                                                   |
| style.fontWeight = 'bolder'        | Marca el texto del elemento como negrita.                                             |
| style.textDecoration = 'underline' | Subraya el texto del elemento.                                                        |

[Tabla con todos los métodos del style.](https://www.w3schools.com/jsref/dom_obj_style.asp)

### DOM: Métodos de clases de un elemento
| Método                       | Descripción                                                               |
|------------------------------|---------------------------------------------------------------------------|
| classList.add('nombre')                | Añade una clase.                                                          |
| classList.remove('nombre')             | Elimina una clase.                                                        |
| classList.item(0)            | Obtiene la primera clase que tenga.                                       |
| classList.contains('nombre') | Devuelve true o false en base a si existe o no la clase.                  |
| classList.toggle('nombre')             | Si la clase no existe la añade, y si existe la elimina.                   |
| classList.toggle('nombre', true)       | Si la clase no existe la añade.                                           |
| classList.toggle('nombre', false)      | Si la clase existe la elimina.                                            |
| classList.replace('uno', 'dos')        | Reemplaza una clase por otra, devuelve true si lo ha realizado con éxito. |

[Documentación con ejemplos.](https://www.w3schools.com/jsref/prop_element_classlist.asp)

### DOM: Creación de elementos
| Método                       | Descripción                                                          | Ejemplo                                      |
|------------------------------|----------------------------------------------------------------------|----------------------------------------------|
| createElement('BUTTON')      | Crear un elemento. En este caso un botón.                            | var btn = document.createElement('BUTTON')   |
| appendChild(element)         | Añadir un elemento al elemento seleccionado.                         | document.body.appendChild(btn)               |
| createTextNode('texto')      | Crear un nodo de texto que después podremos añadir a algún elemento. | var texto = document.createTextNode('Hola!') |

Otros dos métodos de creación de elementosimportantes pero que requieren una explicación y ejemplos más extensos:
- [createDocumentFragment()](https://developer.mozilla.org/es/docs/Web/API/Document/createDocumentFragment)
- [createElementNS() con su explicación](https://developer.mozilla.org/es/docs/Web/API/Document/createElementNS)

### DOM: Métodos de Childs (hijos)
| Método                       | Descripción                                                                                                                                                                                                                                                                                                                  |
|------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| firstChild                   | Devuelve como objeto el primer hijo del nodo especificado.                                                                                                                                                                                                                                                                   |
| lastChild                    | Devuelve como objeto último hijo del nodo especificado.                                                                                                                                                                                                                                                                      |
| firstElementChild            | Devuelve como objeto el primer hijo del nodo especificado, pero a diferencia de firstChild, omitirá los siguientes nodos: #text y comentarios.  Por ejemplo, el simple hecho de haber un salto de línea en el html para que el contenido sea más legible supondrá que exista un nodo #text, y con este método lo evitaremos. |
| lastElementChild             | Devuelve como objeto el último hijo del nodo especificado. Se diferencia de lastChild de la misma manera que firstElementChild se diferencia de firstChild.                                                                                                                                                                  |
| childNodes                   | Devolverá un array que contendrá todos los hijos del nodo especificado.                                                                                                                                                                                                                                                      |
| children                     | Devolverá un array que contendrá todos los hijos del nodo especificado omitiendo los nodos #text y comentarios.                                                                                                                                                                                                              |
| appendChild(element)         | Añadirá el elemento hijo al elemento padre seleccionado. Si tiene varios hijos, lo añadirá al final.                                                                                                                                                                                                                         |
| replaceChild(nuevo, antiguo) | Reemplazará el elemento hijo antiguo por el hijo nuevo en el elemento padre seleccionado.                                                                                                                                                                                                                                    |
| removeChild(element)         | Eliminará el elemento hijo del elemento padre seleccionado.                                                                                                                                                                                                                                                                  |
| hasChildNodes()              | Devolverá true si el elemento padre seleccionado tiene elementos hijos. No omitirá #text ni comentarios                                                                                                                                                                                                                      |

### DOM: Métodos de Parents (padres)
| Método        | Descripción                                           |
|---------------|-------------------------------------------------------|
| parentElement | Devuelve como objeto el padre del hijo especificado.  |
| parentNode    | Devuelve como objeto del padre del hijo especificado. |

La única diferencia entre estos dos métodos es que, si intentamos mirar el padre del elemento raíz, parentNode nos devolverá la instancia document, mientras que parentElement nos devolverá un valor nulo.

```javascript
document.body.parentNode; // El elemento <html>
document.body.parentElement; // El elemento <html>

document.documentElement.parentNode; // El nodo document
document.documentElement.parentElement; // null

console.log(document.documentElement.parentNode === document);  // true
console.log(document.documentElement.parentElement === document);  // false
```

### DOM: Métodos de Siblings (hermanos)
| Método                 | Descripción                                                                                                                                                                 |
|------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| nextSibling            | Devuelve como objeto el siguiente hermano del elemento especificado. Devuelve null si no existe.                                                                            |
| previousSibling        | Devuelve como objeto el anterior hermano del nodo especificado. Devuelve null si no existe.                                                                                 |
| nextElementSibling     | Devuelve como objeto el siguiente hermano del elemento especificado. A diferencia de nextSibling, omitirá los nodos #text y los comentarios. Devuelve null si no existe.    |
| previousElementSibling | Devuelve como objeto el anterior hermano del elemento especificado. A diferencia de previousSibling, omitirá los nodos #text y los comentarios. Devuelve null si no existe. |
  
Nota: Se condiera que dos nodos o elementos son hermanos cuando tienen el mismo padre, es decir, están al mismo nivel.

### DOM: Otros métodos útiles e interesantes

- [closest()](https://developer.mozilla.org/es/docs/Web/API/Element/closest)

### DOM: Más documentación

Enlaces para poder consultar todo lo que quieras sobre DOM, desde su introducción y explicación hasta una lista de sus métodos.

- [Introducción y explicación (utilizar el menú lateral izquierdo)](https://www.w3schools.com/js/js_htmldom.asp)
- [Todos los métodos (utilizar el menú lateral izquierdo)](https://www.w3schools.com/jsref/dom_obj_all.asp)

Está en inglés, si quieres consultar un método en concreto y no comprendes bien del todo su descripción o utilidad, puedes buscar dicho método en concreto en internet y podrás acceder a la documentación en castellano, generalmente en la url https://developer.mozilla.org/es/docs/Web/Reference (donde también puedes acceder y mirar su documentación directamente).

