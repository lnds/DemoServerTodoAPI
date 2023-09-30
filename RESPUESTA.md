Integrantes: Marco Aguilar — Rocío Contreras Aguila


¿En cuantos micro servicios podría descomponer (o agrupar) los endpoints contenidos en el archivo index.js? 


Creemos que se puede descomponer en dos microservicios:

1. Auntenticación
2. Manejo de Actividades específicas o tareas
  
¿Qué problema tienen los endpoints de gestión de usuarios con respecto a la forma estándar de organizar las APIs REST? 

Los endpoints de gestión que normalmente centralizan los CRUDs y los usuarios no son recursos, 
además para este caso se crea un token JWT, por lo tanto no se puede seguir la aplicación de un estandar al pie de la letra.

Por otro lado los endpoints de trabajo con los usuarios en una API REST tienden a ser más complejos por la necesidad 
de manejar la autenticación, la autorización y la gestión de datos sensibles. 

Los desafíos adicionales en la gestión de sesiones, la recuperación de contraseñas y otros flujos que se relacionan directamente con 
la identidad, hacen que esta parte de una API sea más compleja, complicada en comparación con otros endpoints que pueden ser más simples 
en su naturaleza. Esto quiere decir que es importante planificar y diseñar cuidadosamente la gestión de usuarios en una API REST 
para garantizar la seguridad y la eficiencia.
