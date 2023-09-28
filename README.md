# Integrantes:
-Carlos Correa
-Juan Hernandez
-Fernando Sepúlveda
-Sebastián Blanco.

# Respuestas:
1.- La decisión de cuántos microservicios utilizar para una aplicación nativa en la nube depende de varios factores y no se basa únicamente en el número de endpoints. en este caso particular lo separaríamos en 2 microservicios, uno para usuarios y otro para las tareas.

2.- Los endpoints de gestión de usuarios en una aplicación nativa en la nube pueden enfrentar varios problemas con respecto a la forma estándar de organizar las API REST. Como, por ejemplo.
Escalabilidad y rendimiento: en una arquitectura REST estándar, los puntos finales suelen estar agrupados bajo recursos como /usuarios. Esto puede generar problemas de escalabilidad y rendimiento si la aplicación tiene un gran número de usuarios o un alto tráfico. Cada solicitud a /usuariospodría afectar a todos los usuarios, lo que podría resultar en cuellos de botella y un rendimiento deficiente.
Duplicación de Funcionalidad: En una API REST estándar, es posible que debas implementar funciones de gestión de usuarios en Múltiples lugares si tienes diferentes partes de tu aplicación que requieren autenticación y acceso a perfiles de usuario. Esto puede llevar a la duplicación de código ya la falta de coherencia en la gestión de usuarios.
Dificultad en la Evolución: La gestión de usuarios es una funcionalidad que puede evolucionar con el tiempo. Puedes necesitar agregar nuevas características, como autenticación de dos factores o integración con proveedores de identidad externos. En una arquitectura REST estándar, estos cambios pueden ser complicados y afectar a toda la API.

Entre otras.

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

   
# Opcional

Cree otro ReplIT a partir de este repositorio: https://github.com/lnds/DemoTodoAppReactClient.

Modifique el archivo `src/components/const.js` cambiando el valor de la variable `serverApiUrl` por la url del ReplIT donde está corriendo el servidor.

```javascript
const serverApiUrl = 'http://localhost:3001/' // <- modifique esta linea
```

Use esta aplicación para probar sus endpoints.
