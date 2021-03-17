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

Atributos que podemos añadir:
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
## Variables

#### Tipos de variables y su scope (amplitud o rango donde podrán ser utilizadas)

[Hay 3 formas de declarar una variable:](https://www.w3schools.com/js/js_variables.asp)
**let**: declarará una variable que sólo existirá en el bloque donde se haya declarado.
**var**: declarará una variable global (por defecto las variables son tipo var).
**const**: declarará una variable global y constante.
```javascript
const letra = 'a';
var numero = 1;
var numero = 2; // Se sobreescribe sin problemas

if (condicion) {
    console.log(letra); // output: a
    console.log(numero); // output: 2
    
    let resultado = numero + 3;
    console.log(resultado); // output: 5
}

console.log(letra); // output: a
console.log(numero); // output: 2
console.log(resultado); // output: ReferenceError: resultado is not defined

letra = 'b'; // output: TypeError: Assignment to constant variable
```  
Como nota, puedes crear una variable let que se llame igual que una variable var y al hacer referencia a dicho nombre priorizará la variable let, pero no es recomendable, hay que centrarse en hacer un código limpio y **claro**, es decir, fácil de entender, y repetir nombres de variables solo complica las cosas.

----
## Use Strict

Si queremos que sea obligatorio utilizar la indicación **var** para declarar una variable dando uso a las buenas prácticas de programación, tendremos que añadir **'use strict';** al principio del archivo .js (en la primera línea).
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

Si no utilizamos use strict, podremos crear una variable directamente dándole nombre y valor y JS sobreentenderá que estamos creando dicha variable con dicho valor.
En cambio, si utilizamos use strict, JS no nos mimará tanto, por lo que tendremos que ir declarando y concretando cada variable.
Parece que es dar un paso atrás, pero realmente ayuda a la hora de crear un código correcto.

Es muy fácil colarse al escribir el nombre de una variable y escribir dos letras al revés, o acostumbrarse a crear variables sin indicar que son var, haciendo difícil entender de dónde ha salido y en qué momento hemos necesitado dicha variable.
Use strict nos obligará a utilizar "las buenas prácticas" a la hora de programar, haciendo que nuestro código quede más claro y ordenado.


----
## Estructuras de control

#### If... else if... else
```javascript
if (condicion) {
    alert('primera condición verdadera!!');
} else if (condicion2) {
    alert('segunda condición verdadera!');
} else {
    alert('ninguna de las condiciones era verdadera :(');
}
```  

#### Switch
```javascript
switch (accion) {
    case 'saludar': // si accion == 'saludar', ejecutamos el código
        alert('hola!');
        break; // si no añadimos el break, ejecutaría el siguiente case
    case 'despedir':
        alert('adiós!');
        break;
    default:
        alert('acción no contemplada!')
}
```  

#### For (fori)
```javascript
for (var i = 0; i < 10, i++) {
    console.log(`¡Hola! Te he saludado ${i} veces`);
}
```  

#### While
```javascript
var n = 0;
while (n < 7) {
    n++;
    console.log(`¡Hola! Te he saludado ${n} veces`);
}
```  

#### Do While
```javascript
var n = 0;
do {
    n++;
    console.log(`¡Hola! Te he saludado ${n} veces`);
} while (n < 7);
```  

#### For ... in

Podemos utilizarlo de dos formas diferentes:
1- Recorrer las propiedades de un objeto
```javascript
var objeto = {
    nombre: "Daniel",
    edad: 25
};
for (propiedad in objeto) {
    console.log(propiedad); // output: Nombre de la propiedad
    console.log(objeto[propiedad]) // output: Valor de dicha propiedad del objeto
}
```  
__Nota:__ podríamos utilizar objeto.hasOwnProperty(propiedad) para comprobar si en efecto un objeto tiene dicha propiedad.

2- Recorrer las posiciones de un array
```javascript
var lista_personas = [ "Daniel", "María", "Irune", "Aitor" ];
for (posicion in lista_personas) {
    console.log(posicion); // output: Posición que está recorriendo
    console.log(lista_personas[posicion]); // output: Valor de dicha posición en el array
}
```  

#### For ... of

En el For...in estábamos recorriendo y obteniendo las posiciones de un array o el nombre de las propiedades de un objeto. 
Ahora, con el For...of vamos a recorrer directamente los valores.
```javascript
var lista_personas = [ "Daniel", "María", "Irune", "Aitor" ];
for (persona of lista_personas) {
    console.log(persona); // output: Valor -> ejemplo: Daniel
}
```  

#### Try ... catch ... finaly

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

console.log(prueba2());
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
- Si tenemos un trozo de código repetido a lo largo de nuestro desarrollo, deberemos refactorizarlo en una función la cual llamemos desde donde deseemos.
- Un parámetro REST no tiene nada que ver con las API REST, son cosas distintas. Simplemente JavaScript entenderá que cuando introducimos un parámetro REST debe introducir todas las variables "extra" que reciba en un array el cual podremos manejar.

----
## Callbacks

Un **callback** (llamada de vuelta) es una función que recibe como argumento otra función y la ejecuta.

```javascript
function resultado(var1, var2, funcion) {
    return funcion(var1, var2);
}

var sumar = function (n1, n2) {
    return n1 + n2;
}

var multiplicar = function(n1, n2) {
    return n1 * n2;
}

var res = resultado(2, 4, sumar);
console.log(res); // 6

var res = resultado(2, 4, multiplicar);
console.log(res); // 8
``` 

Utilidades de utilizar Callbacks:
- Poder controlar pasar una función como parámetro a otra función (como en el ejemplo).
- Controlar la ejecución asíncrona con callbacks.
- Callbacks para eliminar el conocimiento en las dependencias.

[Puedes ver en profundidad todos los usos de los Callbacks con explicaciones y ejemplos aquí.](https://medium.com/@anamartinezaguilar/callbacks-en-javascript-8deeca9824b40)







