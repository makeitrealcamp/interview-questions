# Node

### ¿Qué es NPM?
NPM (Node Package Manager) es un administrador de paquetes de software para el lenguaje de programación JavaScript. Se utiliza principalmente para instalar y gestionar módulos de código reutilizable que se pueden utilizar en proyectos de JavaScript.

Los módulos de NPM son código JavaScript escrito por otros desarrolladores que se pueden utilizar en tus proyectos. Al utilizar NPM, puedes instalar y utilizar estos módulos de forma fácil y rápida, lo que te permite ahorrar tiempo al no tener que escribir todo el código necesario desde cero.

Para utilizar NPM, primero debes instalar Node.js en tu ordenador. Node.js es un entorno de tiempo de ejecución de JavaScript que te permite ejecutar código JavaScript en tu ordenador, lo que te permite utilizar NPM. Una vez que tienes Node.js instalado, puedes usar el comando npm en tu terminal para instalar y gestionar módulos de NPM.

Ejemplo de uso:

```bash
npm install express
```

Este comando instala el módulo de NPM llamado "express", que es un framework de aplicaciones web para Node.js. Una vez que lo has instalado, puedes utilizar el código de "express" en tu proyecto de JavaScript.

### ¿Qué es un middleware?
Un middleware en Node.js es una función que se ejecuta entre la recepción de una solicitud y la generación de una respuesta. Se utiliza a menudo para realizar tareas comunes, como validar datos o autenticar usuarios, antes de permitir que la solicitud continúe hacia el siguiente componente de la aplicación.

Un middleware puede ser utilizado para realizar una variedad de tareas, como:

- Validar datos de entrada
- Autenticar usuarios
- Establecer encabezados HTTP
- Realizar tareas de seguridad
- Registrar actividad
- Realizar tareas de redirección

Un middleware se define como una función que toma tres argumentos: la solicitud (request), la respuesta (response) y la función next. La función next es una función que se utiliza para pasar el control a la siguiente función en la cadena de middleware.

Aquí hay un ejemplo de un middleware que se utiliza para establecer un encabezado HTTP en todas las respuestas:

```js
app.use(function(req, res, next) {
  res.setHeader('Content-Type', 'application/json');
  next();
});
```

En este ejemplo, el middleware establece el encabezado "Content-Type" en todas las respuestas con el valor "application/json". Luego, llama a la función next para permitir que la solicitud continúe hacia el siguiente componente de la aplicación.

Los middlewares se utilizan a menudo en aplicaciones de Node.js para realizar tareas comunes y ahorrar tiempo al no tener que escribir el mismo código una y otra vez.

### ¿Qué es el **package.json** y **package-lock.json**?

`package.json` es un archivo que se encuentra en la raíz de un proyecto de Node.js y contiene información sobre el proyecto y sus dependencias. Es un archivo de configuración que se utiliza para describir el proyecto y sus dependencias, así como para especificar scripts que se pueden ejecutar en el proyecto.

Aquí hay un ejemplo de lo que podría incluir un archivo `package.json`:

```json
{
  "name": "mi-proyecto",
  "version": "1.0.0",
  "description": "Mi proyecto de Node.js",
  "main": "index.js",
  "scripts": {
    "start": "node index.js"
  },
  "dependencies": {
    "express": "^4.17.1"
  }
}
```

En este ejemplo, el archivo `package.json` incluye información sobre el nombre, la versión y la descripción del proyecto, así como el archivo principal del proyecto (`index.js`). También incluye una sección de scripts con un script llamado "start" que se ejecuta con el comando `npm start`. Finalmente, incluye una sección de dependencias que especifica que el proyecto depende del módulo de NPM "express".

`package-lock.json` es un archivo que se genera automáticamente cuando instalas dependencias en tu proyecto utilizando NPM. Contiene información sobre las dependencias y sus versiones exactas que se han instalado en el proyecto. Esto es útil para asegurar que todos los desarrolladores en un proyecto estén utilizando las mismas versiones de las dependencias, lo que puede ayudar a evitar problemas de compatibilidad.

Cuando instalas una dependencia utilizando NPM, se crea un archivo package-lock.json que incluye información detallada sobre las dependencias y sus versiones exactas. Luego, cuando otro desarrollador clona el proyecto y ejecuta npm install, NPM instalará las dependencias especificadas en el archivo `package-lock.json`, asegurando que todos estén utilizando la misma versión.

En resumen, `package.json` es un archivo de configuración que describe tu proyecto y sus dependencias, mientras que `package-lock.json` es un archivo generado automáticamente que contiene información sobre las dependencias y sus versiones exactas instaladas en el proyecto.

### ¿Qué es un **RESTful API**?

Un API RESTful (Application Programming Interface) es un estilo de arquitectura de API que se basa en los principios del protocolo HTTP y en el estilo arquitectónico REST (Representational State Transfer). Un API RESTful es un conjunto de interfaces de programación de aplicaciones que permite que dos sistemas se comuniquen y compartan datos de manera sencilla y estandarizada.

Las API RESTful siguen un conjunto de principios que definen cómo deben diseñarse y utilizarse. Algunos de estos principios son:

- Utilizar los verbos HTTP (GET, POST, PUT, DELETE) para realizar operaciones CRUD (create, read, update, delete) en los recursos.
- Utilizar URIs (Uniform Resource Identifiers) para identificar recursos.
- Utilizar el formato de intercambio de datos JSON para enviar y recibir datos.
- Utilizar códigos de estado HTTP para indicar el resultado de una solicitud.

Un ejemplo de una API RESTful podría ser una API que exponga una serie de operaciones CRUD para manejar usuarios en una aplicación. Por ejemplo, podrías tener una API que exponga las siguientes operaciones:

- `GET /users`: Obtiene una lista de todos los usuarios.
- `GET /users/{id}`: Obtiene la información del usuario con el ID especificado.
- `POST /users`: Crea un nuevo usuario con la información enviada en el cuerpo de la solicitud.
- `PUT /users/{id}`: Actualiza la información del usuario con el ID especificado con la información enviada en el cuerpo de la solicitud.
- `DELETE /users/{id}`: Elimina el usuario con el ID especificado.

En este ejemplo, cada operación se realiza utilizando un verbo HTTP específico y se accede a los recursos mediante URIs. Los datos se envían y reciben en formato JSON y se utilizan códigos de estado HTTP para indicar el resultado de la solicitud.

En resumen, una API RESTful es un estilo de arquitectura de API que sigue un conjunto de principios y utiliza HTTP y REST para permitir que dos sistemas se comuniquen y compartan datos de manera sencilla y estandarizada.


### ¿Qué es GraphQL?

GraphQL es un lenguaje de consulta y un marco de trabajo creado por Facebook para la recuperación de datos y la manipulación de APIs. Es una alternativa a las APIs RESTful tradicionales y se ha vuelto cada vez más popular en los últimos años debido a su flexibilidad y capacidad para satisfacer las necesidades de datos específicas de los clientes.

En GraphQL, los clientes envían consultas a un servidor que especifican exactamente qué datos necesitan. El servidor responde con los datos solicitados, sin más. Esto es en contraste con las APIs RESTful, donde el cliente solo puede acceder a los datos proporcionados por la API y no puede especificar exactamente qué datos necesita.

Aquí hay un ejemplo de una consulta GraphQL que solicita información sobre un usuario y sus publicaciones:

```graphql
query {
  user(id: 123) {
    name
    posts {
      title
      body
    }
  }
}
```

En esta consulta, se está solicitando información sobre el usuario con el ID 123, incluyendo su nombre y todas sus publicaciones. El servidor respondería con los datos solicitados, como se muestra a continuación:

```graphql
{
  "data": {
    "user": {
      "name": "John Doe",
      "posts": [
        {
          "title": "Mi primer post",
          "body": "Este es mi primer post en mi blog."
        },
        {
          "title": "Mi segundo post",
          "body": "Este es mi segundo post en mi blog."
        }
      ]
    }
  }
}

```

Como puedes ver, GraphQL te permite recuperar solo los datos que necesitas, en lugar de tener que acceder a un conjunto predeterminado de datos proporcionados por la API. Esto puede ser muy útil cuando trabajas con aplicaciones que necesitan acceder a datos de varias fuentes o que tienen requisitos de datos cambiantes.

En resumen, GraphQL es un lenguaje de consulta y marco de trabajo que te permite recuperar y manipular datos de una manera más flexible y personalizada que las APIs RESTful tradicionales.

## HTTP

1. ¿Para qué sirven los métodos HEAD y OPTION?
1. ¿Qué significan los estados 1xx, 2xx, 3xx, 4xx, 5xx?
1. ¿Qué es CORS?
