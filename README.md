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
2. ¿Qué problema tienen los endpoints de gestión de usuarios con respecto a la forma estándar de organizar las APIs REST?

# Respuestas
1.
a) Autenticación y Registro de Usuarios:

/register: Para registrar nuevos usuarios.
/login: Para autenticar a los usuarios.
/verify: Para validar un token JWT (autenticación).

Estos endpoints están relacionados con la autenticación y gestión de usuarios y podrían agruparse en un microservicio de "Autenticación y Usuarios".

b) Gestión de Todos:

/todos: Para crear y listar tareas de usuario.
/todos/:id: Para obtener, actualizar y eliminar tareas específicas.

Estos endpoints están relacionados con la gestión de tareas de usuario y podrían agruparse en un microservicio de "Gestión de Tareas".

c) Documentación Swagger:

/doc: Para servir la documentación Swagger de la API.
La documentación Swagger es independiente de las funcionalidades principales y podría estar en su propio microservicio de "Documentación".

2.
Los problemas en los endpoints de gestión de usuarios son los siguientes:

Endpoint /register:

El endpoint de registro de usuarios debería seguir una convención más estándar, como POST /users, donde /users representa el recurso de usuarios y POST se usa para crear uno nuevo. Esto hace que la API sea más intuitiva y coherente.

Endpoint /login:

El endpoint de inicio de sesión también podría beneficiarse de una convención más estándar, como POST /users/login. Al seguir esta convención, los desarrolladores sabrán que están iniciando sesión en la entidad de usuario.

Endpoint /users:

Aunque este endpoint se encarga de listar todos los usuarios, su nombre sugiere que podría ser utilizado para crear un nuevo usuario (GET para obtener una lista de usuarios). Para listar usuarios, sería más apropiado usar una ruta como GET /users.

Integrantes:
- Ignacio J. González P.

# Opcional

Cree otro ReplIT a partir de este repositorio: https://github.com/lnds/DemoTodoAppReactClient.

Modifique el archivo `src/components/const.js` cambiando el valor de la variable `serverApiUrl` por la url del ReplIT donde está corriendo el servidor.

```javascript
const serverApiUrl = 'http://localhost:3001/' // <- modifique esta linea
```

Use esta aplicación para probar sus endpoints.
