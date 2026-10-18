## VOLUMEN ANÓNIMO
Un volumen anónimo es un volumen gestionado por Docker, el volumen se crea automáticamente sin un nombre específico cuando ejecutas un contenedor. Son útiles cuando deseas almacenar datos temporalmente sin preocuparte por el nombre del volumen. Docker asigna un identificador único en lugar de un nombre. Se utilizan principalmente para almacenamiento temporal. 
**Considerar**
Los datos persisten mientras el contenedor exista, pero son más difíciles de gestionar y referenciar después.

```
docker run -d --name server-nginx -v /usr/share/nginx/html nginx:alpine
```
ó
```
docker run -d --name <nombre contenedor> --mount type=volume,target=<ruta carpeta contenedor> <nombre_imagen>
```
destination, dst, target: La ruta donde se monta el archivo o directorio en el contenedor.
<img width="942" height="853" alt="image" src="https://github.com/user-attachments/assets/53215bb9-57df-4f29-b673-908d9468ff03" />

<img width="936" height="852" alt="image" src="https://github.com/user-attachments/assets/e759a721-2f89-451e-8d3c-583782e2de0b" />

<img width="932" height="841" alt="image" src="https://github.com/user-attachments/assets/a5939da6-52d5-42a6-8055-e6b791fd4b5f" />


### Para eliminar el contenedor y el volumen
```
docker rm -fv server-nginx
```
_esta instrucción elimina el volumen si éste es de tipo anónimo_

# Eliminar todos los volúmenes anónimos (dangling volumes) no utilizados
Los dangling volumes son volúmenes en Docker que no están asociados a ningún contenedor en ejecución. Estos volúmenes se crean cuando se monta un volumen en un contenedor y luego se elimina ese contenedor sin eliminar explícitamente el volumen.
```
docker volume prune
```
<img width="941" height="845" alt="image" src="https://github.com/user-attachments/assets/d77a64fa-40e3-4e96-8e30-c979325456be" />

