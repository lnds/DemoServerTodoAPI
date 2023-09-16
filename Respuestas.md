Integrantes:
Nancy Bernal
Felipe Pérez

¿En cuantos micro servicios podría descomponer (o agrupar) los endpoints contenidos en el archivo index.js?
R: En 2, uno de auntenticación y otro de manejo de tareas
¿Qué problema tienen los endpoints de gestión de usuarios con respecto a la forma estándar de organizar las APIs REST?
R: Los endpoints de gestión centralizan los CRUDs y los usuarios no son recursos, además para este caso se crea un token JWT, por lo tanto no se puede seguir en estandar al pie de la letra.
