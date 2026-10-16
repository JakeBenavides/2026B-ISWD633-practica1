# BIND MOUNT
En un bind mount mapeamos (montar) un directorio o archivo específico del sistema de archivos del host con una parte del sistema de ficheros del contenedor.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen> 
```
ó
```
docker run -d --name <nombre contenedor> --mount type=bind,source=<ruta carpeta host>,target=<ruta carpeta contenedor> <imagen>
```
- destination, dst, target: La ruta donde se monta el archivo o directorio en el contenedor.
- source, src: El origen del montaje.
  
### En tu computador crear una carpeta llamada nginx y dentro de esta carpeta crea otra llamada html. Como se aprecia en la figura.
![Volúmenes](directorio.PNG)

### Crear un contenedor con la imagen nginx:alpine, mapear todos por puertos, para la ruta carpeta host colocar el directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html (esta ruta se obtiene al revisar la documentación de la imagen)
![Volúmenes](volumen-host.PNG)
#### docker run -d --name nginx-bind -p 80:80 -v C:\Users\LENOVO\nginx\html:/usr/share/nginx/html nginx:alpine

### ¿Qué sucede al ingresar al servidor de nginx?
#### En este caso antes de descargar el template como tal nos aparace el error 403 diciendo FORBIDDEN, esto básicamente pasa porque la carpeta de HTML del host se encuentra vacia y esta misma se pone sobre /usr/share/nginx/html del contenedor si esto hace que nginx no encuentre el archivo **index.html** para poder presentarlo

### ¿Qué pasa con el archivo index.html del contenedor?
#### En este caso este se queda oculto por el bind mount, en este caso el contenido de la carpeta del host reemplaza lo que se ve en la ruta dentro de ese contenedor, El index.html original sigue existiendo en la imagen, pero el contenedor no puede acceder a él mientras el montaje esté activo.

### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de tu computador en la carpeta html
### ¿Qué sucede al ingresar al servidor de nginx?
#### En este caso una vez descargado el template y descomprimirlo se muetsra el template en la página recargandola como tal 

### Eliminar el contenedor
#### docker rm -f nginx-bind

### ¿Qué sucede al crear nuevamente un contenedor montado al directorio definidos anteriormente?
#### En este caso al volver a crear de nuevo el contenedor este sigue funcionando y los datos persisten porque en este caso estos están almacenados en el sistema de archivos del host.

