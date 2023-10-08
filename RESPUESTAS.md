¿En cuantos micro servicios podría descomponer (o agrupar) los endpoints contenidos en el archivo index.js?

Usuarios: Agruparía todos los endpoints relacionados con la gestión de usuarios (/register, /login, /users, /verify).

Tareas (Todos): Agruparía todos los endpoints relacionados con la gestión de tareas (/todos y /todos/:id).

Esto te da un total de 2 microservicios principales. 

¿Qué problema tienen los endpoints de gestión de usuarios con respecto a la forma estándar de organizar las APIs REST?

El principal problema es el uso del método OPTIONS para los endpoints, lo cual no es estándar en APIs REST. En REST, se espera que utilices métodos HTTP como GET, POST, PUT, DELETE, etc., que correspondan a las acciones CRUD (Create, Read, Update, Delete). Estos métodos tienen significados específicos que indican la acción que se está realizando, mientras que OPTIONS se usa típicamente para describir las opciones de comunicación para el recurso de destino.
