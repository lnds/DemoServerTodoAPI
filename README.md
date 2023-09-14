# Tarea 1: REST

Haga un fork de este repositorio.

# Preparación

En ReplIT cree un nuevo REPL a partir del repositorio creado con el fork (use el botón `import from GitHub`).

IMPORTANTE: este proceso podría crear un archivo `replit.nix`, asegurese de eliminar ese archivo.

Ingrese a ElephantSQL: https://www.elephantsql.com (ingrese usando GitHub).

Cree una instancia de base de datos.

Ejecute las queries que están en el archivo [`database.sql`](database.sql).

Obtenga el string de conexión desde ElephantSQL (tal como mostró el profesor).

Ahora cree los siguientes SECRETS en Replit:

  - PORT: 3000
  - CONNECTION_URL: coloque aca la url de conexión obgenida de ElephantSQL
  - JWT_SECRET: coloque un valor aleatorio


Ejecute ReplIT presionando el botón `RUN`.


Use [YARC](https://chrome.google.com/webstore/search/yarc) para crear un usuario.
 (También puede usar [`curl`](https://curl.se/)  o [PostMan](https://www.postman.com/)).

# Desafío

Este programa usa el méotodo OPTIONS para todos los endpoints. Debe reemplazarlos por los métodos que corresponden.

Ejemplo, a partir de la linea 85 tenemos este código en el archivo `index.js`:

```javascript
 // verificar usuario
app.options("/login", async (req, res) => {
  // #swagger.description = 'Endpoint para obtener un token de sesión para el usuario'
```

Debe quedar así:

```javascript
 // verificar usuario
app.post("/login", async (req, res) => {
  // #swagger.description = 'Endpoint para obtener un token de sesión para el usuario'
```

En la linea 116 tenemos este código:

```javascript
// List all users
app.options("/users", async (req, res) => {
  // #swagger.description = 'Endpoint para listar todos los usuarios registrados en el sistema'
```

Debe quedar así:

```javascript
// List all users
app.get("/users", async (req, res) => {
  // #swagger.description = 'Endpoint para listar todos los usuarios registrados en el sistema'
```

Haga estas modificaciones y las que corresponden en las lineas: 170, 186, 201, 217 y 235 del archivo `index.js`. 

Debe usar los métodos `post`, `get`, `put`, `delete` según corresponda.

Cuando haya realizado las modificaciones pruébelas con YARC, conteste las preguntas de abajo y mande un Pull Request con sus modificaciones y las respuestas a las preguntas.

# Preguntas

1. ¿En cuantos micro servicios podría descomponer (o agrupar) los endpoints contenidos en el archivo `index.js`?

Se podría agrupar los endpoints en los siguientes microservicios para las 2 áreas principales de funcionalidad de la aplicación: autenticación y gestión de usuarios, así como la gestión de tareas.

* Autenticación y Usuarios:

/register: Registro de usuarios.
/login: Autenticación de usuarios.
/users: Listado de todos los usuarios.
/verify: Validación de token.

* Tareas (Todo):

/todos: Creación de una nueva tarea y listado de todas las tareas del usuario.
/todos/:id: Obtención, actualización y eliminación de una tarea específica por ID.

   
3. ¿Qué problema tienen los endpoints de gestión de usuarios con respecto a la forma estándar de organizar las APIs REST?

la convención de nombres y la semántica de las rutas en una API REST convencional, se utiliza una estructura de rutas que refleja los recursos y las acciones sobre esos recursos. Los nombres de las rutas y los verbos HTTP utilizados se alinean con las operaciones CRUD (Crear, Leer, Actualizar, Eliminar) sobre los recursos. Por ejemplo:

- POST /users: Crear un nuevo usuario.
- GET /users/:id: Obtener un usuario por su ID.
- PUT /users/:id: Actualizar un usuario por su ID.
- DELETE /users/:id: Eliminar un usuario por su ID.

Sin embargo, en tu esta implementación actual, los nombres de las rutas no siguen esta convención estándar.

- /register: Registro de usuarios (Esto debería ser POST /users).
- /login: Autenticación de usuarios (Esto podría ser POST /login).
- /users: Listado de todos los usuarios (Esto podría ser GET /users).
- /verify: Validación de token (Esto podría ser GET /verify o incluso POST /verify si se utiliza para renovar tokens).
   
# Opcional

Cree otro ReplIT a partir de este repositorio: https://github.com/lnds/DemoTodoAppReactClient.

Modifique el archivo `src/components/const.js` cambiando el valor de la variable `serverApiUrl` por la url del ReplIT donde está corriendo el servidor.

```javascript
const serverApiUrl = 'http://localhost:3001/' // <- modifique esta linea
```

Use esta aplicación para probar sus endpoints.
