<div align='center'>
  <img height="60" src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/99/Unofficial_JavaScript_logo_2.svg/480px-Unofficial_JavaScript_logo_2.svg.png">
  <h1>Preguntas de entrevista para Javascript</h1>
</div>

---

## Índice

- [Índice](#índice)
  - [Principiante](#principiante)
    - [¿Cuál es la diferencia entre usar `==` y `===`?](#cual-es-la-diferencia-entre-usar==y===)
    - [¿Cuál es la diferencia entre usar `var`, `let` y `const`?](#cual-es-la-diferencia-entre-usar-var-let-const)
    - [¿Qué es `hoisting`?](#que-es-hoisting)
    - [¿Qué es un `closure`?](#que-es-un-closure)
    - [¿Qué es un `side effect`?](#que-es-un-side-effect)
    - [¿Cómo funciona la herencia en prototipos?](#como-funciona-la-herencia-en-prototipos)
    - [¿Cuáles son las diferencias entre `callback`, `promesas` y `async/await`?](#cuales-son-las-diferencias-entre-callback-promesas-y-asyncawait)
    - [¿Qué es `Type coercion`?](#que-es-type-coercion)
    - [¿Cuáles son las características de una función pura?](#cuales-son-las-caracteristicas-de-una-funcion-pura)
    - [¿Cuál es la diferencia entre asignar un valor o una referencia a una variable?](#cual-es-la-diferencia-entre-asignar-un-valor-o-una-referencia-a-una-variable)
    - [¿Qué es `event delegation`?](#que-es-event-delegation)
    - [¿Qué es `event bubbling`?](#que-es-event-bubbling)
    - [¿Qué es un `polyfill`?](#que-es-un-polyfill)
    - [¿Cuáles son las diferencias entre una función y una función generadora?](#cuales-son-las-diferencias-entre-una-funcion-y-una-funcion-generadora)
    - [¿Cuáles son las diferencias entre una función declaración y una función flecha?](#cuales-son-las-diferencias-entre-una-funcion-declaracion-y-una-funcion-flecha)
    - [¿Qué es el DOM?](#que-es-el-dom)
    - [¿Qué son el `sessionStorage` y el `localStorage`?](#que-son-el-sessionstorage-y-el-localstorage)
---

### Principiante

#### ¿Cuál es la diferencia entre usar `==` y `===`?

El operador de comparacion (`==`) comprueba si sus dos operandos son iguales y devuelve un resultado booleano. A diferencia del **operador de igualdad estricta** (`===`), es que este convierte y compara operandos que son de diferentes tipos.
```js
console.log(1 == 1);
// Expected output: true

console.log('hello' == 'hello');
// Expected output: true

console.log('1' == 1);
// Expected output: true

console.log(0 == false);
// Expected output: true
```

Enlaces de interés:

- [Operador de igualdad regular](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Operators/Equality)
- [Operador de estricta igualdad](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Operators/Strict_equality)

**[⬆ Volver a índice](#índice)**

---

#### ¿Cuál es la diferencia entre usar `var`, `let` y `const`?

##### Var
La declaración `var` se usa para crear variables en JavaScript, con la posibilidad de inicializarlas opcionalmente. A diferencia de `let` y  `const`, `var` tiene alcance de función, no de bloque, lo que significa que una variable declarada con var puede ser accesible dentro de toda la función en la que se declara o globalmente si está fuera de una función. Además, permite redeclaración sin perder su valor actual.

Características clave de var:

**Elevación:** Las declaraciones de variables con var se elevan al inicio de su contexto de ejecución, pero no su inicialización. Esto significa que una variable puede usarse antes de su declaración sin causar un error, aunque el valor inicial será undefined hasta que se le asigne uno explícito.

**Globales implícitas:** Si una variable es asignada sin declaración previa (`var`, `let` o `const`), se convierte en global, lo que puede llevar a comportamientos inesperados y es una práctica desaconsejada, especialmente en modo estricto.

**Configuración:** Las variables declaradas con var no pueden ser eliminadas, a diferencia de las variables globales creadas implícitamente (sin declaración).

**Uso recomendado:** Es preferible evitar var y optar por `let` o `const` en JavaScript moderno para evitar problemas de alcance y facilitar la legibilidad y mantenimiento del código.

##### Let
`Let` permite declarar variables con alcance de bloque. Esto significa que solo están accesibles dentro del bloque `{ }` en el que se declaran, a diferencia de `var`, que tiene alcance de función y puede generar confusión.

Características clave:
**Compatibilidad:** Inicialmente no era estándar en todos los navegadores, pero ahora es ampliamente compatible.
**Alcance de bloque:** Variables declaradas con let solo existen en el bloque donde se definen, ideal para evitar conflictos en bucles y condiciones.
**Zona muerta temporal:** Si una variable let es referenciada antes de su declaración, arroja un ReferenceError.

```js
for (let i = 0; i < 10; i++) {
  console.log(i); // Imprime del 0 al 9
}
console.log(i); // ReferenceError
```
##### Const
`Const` permite crear variables de ámbito de bloque, similares a let, pero con la diferencia de que su valor no puede cambiarse tras su asignación inicial.

Características clave:
**Inmutabilidad del identificador:** El valor asociado a una constante no puede reasignarse, pero si el valor es un objeto, sus propiedades pueden modificarse.
**Ámbito de bloque:** Las constantes declaradas dentro de un bloque sólo existen en ese contexto.
**Inicialización obligatoria:** Es necesario asignarle un valor en el momento de la declaración.
**No redeclaración:** Intentar redeclarar una constante en el mismo ámbito resulta en un error.

```
💡
Nota: Aunque const protege la referencia, no evita cambios en objetos o arrays. Para hacer un objeto completamente inmutable, 
puede usarse Object.freeze().
```

Enlaces de interés:

- [MDN](https://developer.mozilla.org/)

**[⬆ Volver a índice](#índice)**

---
#### ¿Qué es `hoisting`?

`Hoisting` en JavaScript es el comportamiento por el cual las declaraciones de variables y funciones son "elevadas" o ubicadas en memoria durante la fase de compilación, antes de ejecutar el código, aunque su posición física en el código permanezca igual.

Conceptos clave:

Funciones: Puedes llamar a una función antes de declararla, ya que las declaraciones de funciones se almacenan en memoria antes de la ejecución.
```js
nombreDelGato("Dumas"); // Llama a la función antes de declararla

function nombreDelGato(nombre) {
  console.log("El nombre de mi gato es " + nombre);
}
// Output: "El nombre de mi gato es Dumas"
```
Variables: Las declaraciones de variables (var) también se elevan, pero solo la declaración, no la inicialización. Esto significa que acceder a una variable antes de inicializarla dará undefined.

```js
var x = 5;

(function () {
  console.log("x:", x); // undefined, ya que solo se elevó la declaración, no la asignación
  var x = 10;
  console.log("x:", x); // 10
})();
```
```
💡
Nota: En este caso, y es undefined al acceder a ella antes de la inicialización, ya que solo su declaración se elevó, 
no su asignación.
```

**[⬆ Volver a índice](#índice)**

---
#### ¿Qué es un `closure`?

Un `closure` en JavaScript es una combinación de una función y su contexto léxico, lo que significa que la función puede acceder a variables definidas en su ámbito externo, incluso después de que la función externa haya terminado de ejecutarse. Esto permite mantener y manipular valores privados en JavaScript, algo que otros lenguajes logran mediante métodos privados.

Un `closure` se crea cuando una función devuelve otra función interna que recuerda el entorno en el que fue creada. Por ejemplo:

```js
function makeAdder(x) {
  return function(y) {
    return x + y;
  };
}

const add5 = makeAdder(5);
console.log(add5(2)); // 7
```
Aquí, add5 mantiene un `closure` sobre makeAdder, y la variable x sigue accesible dentro de add5.

Los `closure` también pueden emular métodos privados y encapsulación, creando funciones con su propio ámbito léxico que mantienen sus propios valores independientes. Esto es muy útil en programación orientada a eventos y en la manipulación de datos privados sin exponerlos.

**[⬆ Volver a índice](#índice)**

---
#### ¿Qué es un `side effect`?

En programación, un **side effect** es cualquier operación que altera el estado fuera del alcance de una función. Por ejemplo:

- `(x, y) => x + y` no tiene efectos secundarios, ya que no modifica el estado externo.
- `nombre = ""; (value) => nombre = value;` sí produce un efecto secundario al modificar la variable `nombre` fuera de su propio alcance.

**[⬆ Volver a índice](#índice)**

---
#### ¿Cómo funciona la herencia en prototipos?

En programación, **herencia** permite reutilizar y extender el código al transmitir características de un "padre" a un "hijo". En JavaScript, la herencia se implementa mediante **prototipos**: cada objeto tiene un enlace a un objeto prototipo, formando una cadena de prototipos que termina en `null`. A diferencia de lenguajes basados en clases, JavaScript es dinámico y no utiliza despacho estático, lo que permite mayor flexibilidad.

**Cadena de Prototipos y Herencia de Propiedades**
Al intentar acceder a una propiedad en un objeto:
- JavaScript busca primero en el objeto.
- Si no encuentra la propiedad, busca en la cadena de prototipos hasta encontrarla o llegar a `null`.

Ejemplo:

```js
const o = {
  a: 1,
  b: 2,
  __proto__: { b: 3, c: 4 },
};

console.log(o.a); // 1
console.log(o.b); // 2 (sombras sobre el prototipo)
console.log(o.c); // 4 (heredado del prototipo)
console.log(o.d); // undefined
```
**Métodos y Herencia de Funciones**
En JavaScript, los métodos son simplemente funciones añadidas a un objeto. Al ejecutarlos, this hace referencia al objeto desde el cual se llama, no al prototipo donde la función se define.

**Constructores y prototype**
Las funciones constructoras en JavaScript usan una propiedad prototype que, al crear una nueva instancia con new, se copia en la propiedad [[Prototype]] de esa instancia. Todas las instancias comparten el mismo prototipo, permitiendo que métodos y propiedades definidas en prototype se compartan entre instancias.

**[⬆ Volver a índice](#índice)**


---
#### ¿Cuáles son las diferencias entre `callback`, `promesas` y `async/await`?

1. Callback
Una función callback es una función pasada como argumento a otra función, que luego es ejecutada dentro de esa función externa. Se usa principalmente para manejar la finalización de operaciones asincrónicas.

Ventajas: Permite gestionar el flujo de ejecución después de completar una operación.
Desventajas: Puede llevar a problemas de callback hell si no se manejan adecuadamente.

Ejemplo:

```js
function saludar(nombre) {
  alert("Hola " + nombre);
}

function procesarEntradaUsuario(callback) {
  var nombre = prompt("Por favor ingresa tu nombre.");
  callback(nombre);
}

procesarEntradaUsuario(saludar);
```
2. Promesas (Promises)
Una promesa es un objeto que representa la terminación o el fracaso de una operación asincrónica. En lugar de pasar una función de callback, las promesas devuelven un objeto con métodos como .then() para manejar el éxito o el error.

Ventajas: Mejora la legibilidad del código y permite el encadenamiento de operaciones asincrónicas.
Desventajas: Puede volverse compleja cuando se manejan múltiples promesas a la vez.

3. Async/Await
Async/await es una sintaxis que simplifica el manejo de promesas, haciendo que el código asíncrono se vea y se comporte de manera similar al código síncrono. async se usa para declarar una función que devuelve una promesa, y await se usa para esperar la resolución de una promesa dentro de esa función.

Ventajas: Simplifica la escritura y comprensión de código asíncrono, evitando el encadenamiento de .then().
Desventajas: Aún depende de las promesas, por lo que puede haber problemas si no se maneja correctamente.
Resumen de Diferencias:
Callbacks: Funciones pasadas como parámetros, ejecutadas al finalizar una operación asincrónica.
Promesas: Representan una operación asincrónica que se resuelve en el futuro, mejorando la gestión de errores y el encadenamiento.
Async/Await: Sintaxis que facilita el manejo de promesas de forma síncrona, haciendo el código más limpio y fácil de leer.

**[⬆ Volver a índice](#índice)**

---
#### ¿Qué es `Type coercion`?

Type coercion es la conversión automática o implicita de valores de un tipo de dato a otro (Ejemplo: de cadena de texto a número). La conversión es similar a la coerción porque ambas convierten valores de un tipo de dato a otro pero con una diferencia clave - la coerción es implícita mientras que la conversión puede ser implícita o explícita.

Ejemplo:

```js
const valor1 = "5";
const valor2 = 9;
let suma = valor1 + valor2;

console.log(suma);
```
En el ejemplo anterior, JavaScript ha coercido el 9 de número a cadena de texto y luego ha concatenado los dos valores resultando en una cadena de texto de 59. JavaScript tuvo la opción de coercer a cadena de texto o número y decidió usar número.

El compilador pudo haber coercido el 5 a un número y retornar el valor de 14, pero no lo hizo. Para retornar ese resultado, tendrías que convertir explícitamente el 5 a un número usando el método Number():
```js
sumar = Number(valor1) + valor2;

``` 

**[⬆ Volver a índice](#índice)**

---
#### ¿Cuáles son las características de una función pura?

En programación, **herencia** permite reutilizar y extender el código al transmitir características de un "padre" a un "hijo". En JavaScript, la herencia se implementa mediante **prototipos**: cada objeto tiene un enlace a un objeto prototipo, formando una cadena de prototipos que termina en `null`. A diferencia de lenguajes basados en clases, JavaScript es dinámico y no utiliza despacho estático, lo que permite mayor flexibilidad.

**Cadena de Prototipos y Herencia de Propiedades**
Al intentar acceder a una propiedad en un objeto:
- JavaScript busca primero en el objeto.
- Si no encuentra la propiedad, busca en la cadena de prototipos hasta encontrarla o llegar a `null`.

Ejemplo:

```js
const o = {
  a: 1,
  b: 2,
  __proto__: { b: 3, c: 4 },
};

console.log(o.a); // 1
console.log(o.b); // 2 (sombras sobre el prototipo)
console.log(o.c); // 4 (heredado del prototipo)
console.log(o.d); // undefined
```
**Métodos y Herencia de Funciones**
En JavaScript, los métodos son simplemente funciones añadidas a un objeto. Al ejecutarlos, this hace referencia al objeto desde el cual se llama, no al prototipo donde la función se define.

**Constructores y prototype**
Las funciones constructoras en JavaScript usan una propiedad prototype que, al crear una nueva instancia con new, se copia en la propiedad [[Prototype]] de esa instancia. Todas las instancias comparten el mismo prototipo, permitiendo que métodos y propiedades definidas en prototype se compartan entre instancias.

**[⬆ Volver a índice](#índice)**


---
#### ¿Cuál es la diferencia entre asignar un valor o una referencia a una variable?

En JavaScript, una variable es un contenedor para almacenar datos, los cuales pueden ser valores primitivos (números, cadenas) o no primitivos (objetos, arrays, funciones). La manera en que se pasa una variable a una función —por valor o por referencia— afecta si los cambios realizados dentro de la función impactan fuera de ella.

**Diferencias entre Pasar por Valor y por Referencia**
Pasar por Valor: Se refiere a los valores primitivos. Cuando una variable se pasa por valor, cualquier modificación dentro de la función no afecta el valor original fuera de la función.

Ejemplo:

```js
let numero = 21;
const funcionValor = (value) => {
  value = value * 10;
  console.log(`Dentro de la función, value es ${value}`);
};

funcionValor(numero);
console.log(`Fuera de la función, numero es ${numero}`);
// Resultado:
// Dentro de la función, value es 210
// Fuera de la función, numero es 21
```
Pasar por Referencia: Se refiere a los valores no primitivos (objetos, arrays). Cuando se pasa una variable por referencia, los cambios dentro de la función afectan el valor fuera de la función.

Ejemplo:

```js
let arrNumeros = [21];
const funcionReferencia = (value) => {
  value[0] = value[0] * 10;
  console.log(`Dentro de la función, value[0] es ${value[0]}`);
};

funcionReferencia(arrNumeros);
console.log(`Fuera de la función, arrNumeros[0] es ${arrNumeros[0]}`);
// Resultado:
// Dentro de la función, value[0] es 210
// Fuera de la función, arrNumeros[0] es 210

```
- **Valor:** Cambios internos no afectan el valor externo.
- **Referencia:** Cambios internos afectan el valor externo.

**[⬆ Volver a índice](#índice)**


---
#### ¿Qué es `event delegation`?

En JavaScript, cuando un evento se activa en un elemento, este se propaga hacia arriba en el árbol DOM, desde el elemento activado hacia sus elementos padres, ancestros y hasta el elemento raíz (html).

Ejemplo:

```html
<div>
  <span>
    <button>Click Me!</button>
  </span>
</div>
```
En este ejemplo, el botón se encuentra dentro de un `span`, que a su vez está dentro de un `div`. Al hacer clic en el botón, el evento se propaga, alcanzando también al `span` y al `div`.

**Cadena de Prototipos y Herencia de Propiedades**
Al intentar acceder a una propiedad en un objeto:
- JavaScript busca primero en el objeto.
- Si no encuentra la propiedad, busca en la cadena de prototipos hasta encontrarla o llegar a `null`.

**Delegación de Eventos**
Con la delegación de eventos, se puede manejar el evento de un elemento hijo en su elemento padre. Esto permite que un solo listener en el elemento padre capture eventos de múltiples elementos hijos.

Ejemplo:

```js
const div = document.getElementsByTagName("div")[0];

div.addEventListener("click", (event) => {
  if(event.target.tagName === 'BUTTON') {
    console.log("button was clicked");
  }
});
```
En este caso, el `div` maneja el evento de clic, y con event.target.tagName se verifica si el elemento que recibió el clic es un BUTTON.

**Beneficios de la Delegación de Eventos**
La delegación permite crear menos listeners y escribir código más limpio. Por ejemplo, en lugar de añadir listeners a cada botón:

Ejemplo:

```js
const buttons = document.querySelectorAll('button');

buttons.forEach(button => {
  button.addEventListener("click", (event) => {
    console.log(event.target.innerText);
  });
});
```
Se puede gestionar todo desde el elemento padre común:

```js
const div = document.querySelector('div');

div.addEventListener("click", (event) => {
  if(event.target.tagName === 'BUTTON') {
    console.log(event.target.innerText);
  }
});
```
Ahora, al hacer clic en cualquier botón dentro del  `div`, se registra su texto en la consola sin necesidad de agregar un listener para cada botón. Además, si se añaden nuevos botones dentro del  `div`, el mismo código seguirá funcionando.

**Conclusión**

La delegación de eventos permite manejar eventos en un solo lugar, facilita la adición o eliminación de elementos y reduce la cantidad de listeners en el DOM. Esto es posible gracias a la propagación de eventos, que permite que los eventos de elementos hijos lleguen a los elementos padres y ancestros.

**[⬆ Volver a índice](#índice)**


---
#### ¿Qué es `event bubbling`?

HTML recibe diversos eventos como `click`, `blur`, `scroll`, entre otros. Uno de los comportamientos comunes de estos eventos es el **Evento Bubbling**. Aquí explicaremos en qué consiste este concepto.

## ¿Qué es el Evento Bubbling?

El **Evento Bubbling** ocurre cuando un evento en un elemento HTML se propaga hacia arriba en el árbol DOM, alcanzando sus elementos padres y ancestros hasta el nodo raíz (`html`). Es el comportamiento predeterminado de los eventos en el DOM, a menos que la propagación se detenga.

Ejemplo:

```html
<body>
  <div>
    <span>
      <button>Click me!</button>
    </span>
  </div>
</body>
```
Este árbol DOM tiene una estructura jerárquica donde `button` es hijo de `span`, `span` es hijo de `div` y `div` es hijo de `body`. Cuando se hace clic en el botón, el evento click se propaga hacia arriba, activando los eventos de `span`, `div`, y `body`.

```js
const body = document.getElementsByTagName("body")[0];
const div = document.getElementsByTagName("div")[0];
const span = document.getElementsByTagName("span")[0];
const button = document.getElementsByTagName("button")[0];

body.addEventListener('click', () => console.log("se hizo clic en el body"));
div.addEventListener('click', () => console.log("se hizo clic en el div"));
span.addEventListener('click', () => console.log("se hizo clic en el span"));
button.addEventListener('click', () => console.log("se hizo clic en el button"));

```
Al hacer clic en el button, la consola muestra:

```css
se hizo clic en el button
se hizo clic en el span
se hizo clic en el div
se hizo clic en el body
```

**Cómo Detener el Evento Bubbling**
Para evitar la propagación de eventos, se utiliza el método stopPropagation() del objeto event.

Ejemplo:

```js
button.addEventListener("click", (event) => {
  event.stopPropagation();
  console.log("se hizo clic en el button");
});
```
Con stopPropagation(), el clic en el botón solo activa su propio evento y no se propaga a los elementos padres.

**Conclusión**
El Evento Bubbling permite que los eventos se propaguen hacia arriba en el DOM, lo que facilita el manejo de eventos desde elementos padres. Sin embargo, en casos donde deseas que solo un elemento maneje el evento, puedes usar stopPropagation() para detener la propagación.
stopPropagation y preventDefault son métodos útiles del objeto event para manejar comportamientos predeterminados en el DOM.

**[⬆ Volver a índice](#índice)**


---
#### ¿Qué es un `polyfill`?

Un **polyfill** es un fragmento de código que proporciona funcionalidades que un navegador antiguo no soporta de forma nativa. Como lo definió Remy Sharp, quien acuñó el término, es como un parche que otorga al navegador capacidades adicionales.


**¿Para qué sirve un Polyfill?**
Si trabajas con características modernas (por ejemplo, métodos de HTML5 o JavaScript) que no están disponibles en todos los navegadores, puedes usar un polyfill para añadir soporte. Por ejemplo, si un método de array no está implementado en un navegador antiguo, un polyfill puede suplir esa carencia.

**¿Dónde Encontrar Polyfills?**
Uno de los mejores recursos para encontrar polyfills es [Mozilla Developer Network (MDN)](https://developer.mozilla.org). También existen repositorios en línea donde puedes encontrar polyfills específicos para diversas funcionalidades.


**¿Por Qué Son Útiles?**
Los polyfills son esenciales para asegurar que tu sitio web funcione en todos los navegadores soportados, proporcionando una experiencia de usuario uniforme, especialmente al utilizar características modernas no compatibles con algunos navegadores.

**Consideraciones**
Aunque los polyfills son muy útiles, no son una solución universal. Algunas características pueden no ser "polyfillable", y en esos casos podrías considerar una **degradación elegante**, en la que ciertas funcionalidades no esenciales simplemente se desactivan en navegadores que no las soportan. Además, incluye solo los polyfills necesarios para mantener tu sitio optimizado y eficiente.

**[⬆ Volver a índice](#índice)**


---
#### ¿Cuáles son las diferencias entre una función y una función generadora?

**Función normal**
Una función en JavaScript se utiliza para encapsular código que puede ser ejecutado varias veces. Las funciones normales ejecutan todas sus instrucciones y devuelven un valor (si se especifica con return) cuando son llamadas.

**Función generadora**
Una función generadora, en cambio, es un tipo especial de función que puede pausar y reanudar su ejecución. Estas funciones utilizan yield en lugar de return, lo que permite "devolver" múltiples valores, uno a la vez, mientras recuerdan su estado para cuando se reanuden.

**Sintaxis**
- Función normal: se define utilizando la palabra clave function.
- Función generadora: se define con la palabra clave function seguida de un asterisco *.

**Comportamiento**
- Una función normal se ejecuta completamente desde el inicio hasta el final y devuelve un solo valor (o undefined si no tiene un return).
- Una función generadora puede pausar su ejecución en cada yield y reanudarse desde ese punto cuando sea necesario.

Las funciones generadoras son ideales para manejar secuencias de datos y listas perezosas (lazy lists), mientras que las funciones normales son útiles cuando el cálculo o tarea deben completarse de una sola vez.

**[⬆ Volver a índice](#índice)**


---
#### ¿Cuáles son las diferencias entre una función declaración y una función flecha?

Las principales diferencias entre una función declaración y una función flecha son:

**Sintaxis**

- Las funciones declaración tienen una sintaxis más extensa. Se declaran con la palabra clave `function`, seguidas de un nombre (opcional en expresiones de función) y su cuerpo.
- Las funciones flecha usan una sintaxis más corta y nunca llevan nombre explícito, lo que las hace anónimas. Se declaran con `=>`(flecha), lo que las hace ideales para callbacks y expresiones de función simples

Ejemplo:

```js
// Función declaración
function sumar(a, b) {
  return a + b;
}

// Función flecha
const sumar = (a, b) => a + b;

```

**Comportamiento de `this`**

- Las funciones declaración crean su propio this, que depende de cómo se llame la función (por ejemplo, en un objeto o en modo global).
- Las funciones flecha no crean su propio this; en lugar de eso, heredan el this del contexto léxico en el que se encuentran. Esto significa que el valor de this en una función flecha será el mismo que el this del contexto en el que fue definida, lo cual es útil en callbacks y métodos anidados.

Ejemplo:

```js
function Persona() {
  this.edad = 0;

  // Función declaración: crea su propio `this`
  setInterval(function() {
    this.edad++; // `this` apunta al objeto global en modo no estricto
  }, 1000);
}

function PersonaFlecha() {
  this.edad = 0;

  // Función flecha: hereda `this` de PersonaFlecha
  setInterval(() => {
    this.edad++; // `this` apunta al objeto `PersonaFlecha`
  }, 1000);
}
```

**Uso de `arguments`**

- Las funciones declaración tienen acceso a un objeto arguments que contiene todos los parámetros pasados a la función, útil en funciones que reciben un número variable de argumentos.
- Las funciones flecha no tienen su propio objeto arguments. Si necesitan acceder a los argumentos, deben usar un rest parameter (...args) para capturarlos.

Ejemplo:

```js
function declarar() {
  console.log(arguments); // Función declaración tiene `arguments`
}

const flecha = () => {
  console.log(arguments); // Error: `arguments` no está definido
};
```
**Uso de new (Constructor):**
- Las funciones declaración pueden ser invocadas con new para crear instancias (constructores).
- Las funciones flecha no pueden usarse como constructores y generarán un error si se intenta llamarlas con new.

**Hoisting**
- Las funciones declaración están sujetas a hoisting, lo que significa que se pueden llamar antes de su declaración en el código.
- Las funciones flecha asignadas a una variable solo estarán disponibles después de la declaración debido a la forma en que se inicializan las variables const o let.

Estas diferencias hacen que las funciones flecha sean preferibles en algunos contextos, especialmente en programación funcional y cuando se necesita un this fijo, mientras que las funciones declaración siguen siendo útiles para funciones de propósito general y constructores.

**[⬆ Volver a índice](#índice)**


---
#### ¿Qué son el `sessionStorage` y el `localStorage`?

`sessionStorage` y `localStorage` son propiedades del objeto Storage en JavaScript que permiten almacenar datos de manera local en el navegador. Aunque son similares, tienen diferencias importantes en términos de duración y accesibilidad de los datos almacenados:

**Duración del almacenamiento**

- `sessionStorage`: Almacena datos solo durante la sesión de la página. Los datos se eliminan automáticamente cuando se cierra la pestaña o ventana del navegador que los creó. Esto lo hace ideal para almacenar información temporal que solo debe durar mientras la página está abierta.
- `localStorage`: Almacena datos de manera persistente, es decir, los datos no tienen una fecha de expiración y permanecen en el navegador incluso si este se cierra o se reinicia. Es útil para almacenar datos que deben ser accesibles en futuras visitas al sitio.

**Alcance entre pestañas y ventanas**

- `sessionStorage`: Los datos almacenados están limitados a la pestaña o ventana específica que los creó. Si se abre una nueva pestaña o ventana en el mismo sitio, no compartirá los datos de sessionStorage de la pestaña original.
- `localStorage`: Los datos son accesibles desde todas las pestañas o ventanas que compartan el mismo origen (misma combinación de protocolo, host y puerto). Esto permite que los datos persistan y sean compartidos en distintas instancias de una misma aplicación en el navegador.

Ejemplo:

```js
// sessionStorage
sessionStorage.setItem("username", "Alice");  // Almacena un valor temporalmente
console.log(sessionStorage.getItem("username"));  // Recupera el valor

// localStorage
localStorage.setItem("username", "Bob");  // Almacena un valor de manera persistente
console.log(localStorage.getItem("username"));  // Recupera el valor

```

**Limitaciones**
 Ambos almacenes solo aceptan datos en formato de cadena de texto. Si se necesita almacenar objetos u otros tipos de datos, es necesario convertirlos a una cadena con JSON.stringify() y, al recuperar los datos, convertirlos de vuelta con JSON.parse().

**Ventajas**
- `sessionStorage` es útil para datos temporales y específicos de una sesión de usuario en una página.
- `localStorage` permite mantener datos persistentes que los usuarios pueden volver a consultar sin necesidad de recuperarlos de un servidor.

Ambos métodos ofrecen una manera eficiente de almacenar datos sin necesidad de bases de datos o cookies, mejorando la experiencia del usuario y la optimización de datos en el lado del cliente.

**[⬆ Volver a índice](#índice)**


---
#### ¿Cuáles son las características de una función pura?

En programación, **herencia** permite reutilizar y extender el código al transmitir características de un "padre" a un "hijo". En JavaScript, la herencia se implementa mediante **prototipos**: cada objeto tiene un enlace a un objeto prototipo, formando una cadena de prototipos que termina en `null`. A diferencia de lenguajes basados en clases, JavaScript es dinámico y no utiliza despacho estático, lo que permite mayor flexibilidad.

**Cadena de Prototipos y Herencia de Propiedades**
Al intentar acceder a una propiedad en un objeto:
- JavaScript busca primero en el objeto.
- Si no encuentra la propiedad, busca en la cadena de prototipos hasta encontrarla o llegar a `null`.

Ejemplo:

```js
const o = {
  a: 1,
  b: 2,
  __proto__: { b: 3, c: 4 },
};

console.log(o.a); // 1
console.log(o.b); // 2 (sombras sobre el prototipo)
console.log(o.c); // 4 (heredado del prototipo)
console.log(o.d); // undefined
```
**Métodos y Herencia de Funciones**
En JavaScript, los métodos son simplemente funciones añadidas a un objeto. Al ejecutarlos, this hace referencia al objeto desde el cual se llama, no al prototipo donde la función se define.

**Constructores y prototype**
Las funciones constructoras en JavaScript usan una propiedad prototype que, al crear una nueva instancia con new, se copia en la propiedad [[Prototype]] de esa instancia. Todas las instancias comparten el mismo prototipo, permitiendo que métodos y propiedades definidas en prototype se compartan entre instancias.

**[⬆ Volver a índice](#índice)**


---

Mas preguntas :

## TypesScript

1. ¿Qué es una interface?
1. ¿Qué es **duck typing**?
1. ¿Cómo nos ayuda typescript en el proceso de desarrollo?
1. ¿Qué es un `enum`?
1. ¿Qué son métodos **privados**, **protegidos**, y **publicos**?
1. ¿Qué son métodos **estaticos**?
1. ¿Qué son los `tuples`?

---

Enlaces de referencia:

- [Developer mozilla - Learn Javascript](https://developer.mozilla.org/es/docs/Learn/JavaScript)
- [Javascript.info](https://es.javascript.info/)
- [freecodecamp - Learn Javascript](https://www.freecodecamp.org/)
- [W3C - JavaScript:](https://www.w3.org/standards/) 