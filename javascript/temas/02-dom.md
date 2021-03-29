## DOM (Document Object Model)

HTML es un lenguaje de etiquetado padre-hijo, es decir, existe una etiqueta general y dentro de esta etiqueta general se irán generando hijos con los distintos elementos.
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
Body del documento HTML:
```html
<body>
    <div id="div1"></div>
    <p class="parrafo1"></p>
    <p class="parrafo1"></p>
</body>
```

Código javascript
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
```

Este ejemplo ha sido un ejemplo muuuy breve y simple, donde podemos observar cómo buscar un elemento por su ID, modificar su contenido y también cómo recoger en un array todos los elementos de una clase.

Lista de métodos de uso habitual:

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
| setAttribute("type", "valor") | Crea el atributo y le asigna el valor. Si el atributo ya existía, reemplaza su valor.                                                                    |
| getAttribute("type")          | Devuelve el valor del atributo. Si el atributo no existe, devolverá null.                                                                                |
| removeAttribute("type")       | Elimina el atributo.                                                                                                                                     |

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
| accept      | Si el atributo es tipo file, se puede configurar qué archivos aceptará únicamente. Ejemplo: accept="image/png"                            |
| form        | Se le puede asignar un formulario a un botón para que al presionarlo funcione como submit del mismo aún sin estar dentro del propio form. |
| minLength   | Define la cantidad mínima de caracteres necesarios.                                                                                       |
| maxLength   | Define la cantidad máxima de caracteres admitidos.                                                                                        |
| placeholder | Funciona como un hint, es decir, sirve para sugerir o indicar qué debería introducir.                                                     |
| required    | Su valor será true o false y definirá si el input es obligatorio o no.                                                                    |

### DOM: Configurar el atributo Style
Puedes configurarlo línea a línea a través de código JavaScript. Algunos ejemplos:
| Método                                      | Descripción                                                                           |
|---------------------------------------------|---------------------------------------------------------------------------------------|
| elemento.style.color = "#32b"               | Le asigna el color #32b al elemento.                                                  |
| elemento.style.padding = "30px"             | Asigna un padding de 30px alrededor del elemento.                                     |
| elemento.style.fontSize = "32px"            | Asigna un tamaño de fuente de 32px.                                                   |
| elemento.style.fontWeight = "bolder"        | Marca el texto del elemento como negrita.                                             |
| elemento.style.textDecoration = "underline" | Subraya el texto del elemento.                                                        |

[Tabla con todos los métodos del style.](https://www.w3schools.com/jsref/dom_obj_style.asp)

### DOM: Añadir, eliminar, obtener, comprobar y reemplazar clases
| Método                       | Descripción                                                               |
|------------------------------|---------------------------------------------------------------------------|
| add("nombre")                | Añade una clase.                                                          |
| remove("nombre")             | Elimina una clase.                                                        |
| classList.item(0)            | Obtiene la primera clase que tenga.                                       |
| classList.contains("nombre") | Devuelve true o false en base a si existe o no la clase.                  |
| toggle("nombre")             | Si la clase no existe la añade, y si existe la elimina.                   |
| toggle("nombre", true)       | Si la clase no existe la añade.                                           |
| toggle("nombre", false)      | Si la clase existe la elimina.                                            |
| replace("uno", "dos")        | Reemplaza una clase por otra, devuelve true si lo ha realizado con éxito. |

[Documentación con ejemplos.](https://www.w3schools.com/jsref/prop_element_classlist.asp)

### DOM: Creación de elementos

