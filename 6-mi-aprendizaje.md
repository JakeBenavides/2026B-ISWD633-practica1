# COMPLETAR  
Comparando sus conocimientos antes de hacer la práctica con sus conocimientos después de hacer la tarea, explicar los principales aprendizajes logrados para beneficio de su formación profesional.  
Si solucionó un problema presentado o utilizó otros comandos que no se mencionan al realizar la práctica también se debe documentar.


Comparación de conocimientos y aprendizajes

Pensaba que al eliminar un contenedor se perdía toda su información y configuración, pero despues del rpimer ejercicio aprendí que los datos pueden guardarse fuera del contenedor para que persistan
Bind mount: vincula una carpeta de mi computador con una del contenedor. Al eliminar y volver a crear los contenedores de WordPress y MySQL, la página y la configuración seguían ahí.
Volumen nombrado: volumen gestionado por Docker e identificado con un nombre único, sin indicar ruta del host. Lo usé con Postgres y Drupal.
Volumen anónimo: Docker lo crea automáticamente sin nombre específico, útil para almacenamiento temporal. Se elimina con docker rm -fv o con docker volume prune si quedó huérfano.

También aprendí a conectar contenedores en una red propia usando el nombre del contenedor en lugar de la IP.

Problemas solucionados
Template en subcarpeta: nginx no lo mostraba; moví los archivos a la carpeta html con Move-Item.
Postgres se detenía solo: la imagen nueva cambió la ruta de datos; usé /var/lib/postgresql en lugar de /var/lib/postgresql/data.

Los comandos adicionales que usé
docker ps -a, docker rm -f, docker network rm, docker volume ls, docker volume prune, docker inspect.
