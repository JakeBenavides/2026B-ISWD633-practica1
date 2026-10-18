## Esquema para el ejercicio
![Imagen](esquema-ejercicio3.PNG)

### Crear red net-wp
#### docker network create net-wp

### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio carpeta del contenedor (a) es "/var/lib/mysql"

Ruta carpeta host: .../ejercicio3/db

### ¿Qué contiene la carpeta db del host?
#### Para inicial la carpeta se encuentra vacia, porque todavia como tal no se ah creado el contenedor de MYSQL, una vez que se inicia el SQL se guardan los archivos de las bases de datos

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
#### docker run -d --name mysql-wp --network net-wp -e MYSQL_ROOT_PASSWORD=root123 -e MYSQL_DATABASE=wordpress -e MYSQL_USER=jake -e MYSQL_PASSWORD=1234 -v C:\Users\LENOVO\ejercicio3\db:/var/lib/mysql mysql:8

### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
#### En este caso la carpeta ya no está vacia, ya que contiene los archivos generados por el MySQL como por ejemplo mysql y otras y en wordpress en cambio sarchivos com ibdata1 y otros, Esto ocurre porque el bind mount enlaza /var/lib/mysql del contenedor con la carpeta db del host, y MySQL guarda ahí su información.

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
#### COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio la carpeta del contenedor (b) es (/var/www/html)
Ruta carpeta host: .../ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
#### docker run -d --name wordpress-wp --network net-wp -p 9500:80 -e WORDPRESS_DB_HOST=mysql-wp -e WORDPRESS_DB_USER=jake -e WORDPRESS_DB_PASSWORD=1234 -e WORDPRESS_DB_NAME=wordpress -v C:\Users\LENOVO\ejercicio3\www:/var/www/html wordpress

### Personalizar la apariencia de wordpress y agregar una entrada
#### Se ingresó a http://localhost:9500, se completó la instalación de WordPress, se cambió el estilo del sitio desde el Editor del sitio y se publicó una nueva entrada.
<img width="957" height="969" alt="image" src="https://github.com/user-attachments/assets/c5e15c6c-8397-4d86-a089-f151a386eb01" />

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?
#### Se eliminaron los contenedores con docker rm -f wordpress-wp mysql-wp y se volvieron a crear con los mismos comandos docker run. El sitio quedó exactamente igual: se conservaron la apariencia personalizada, la entrada publicada y el usuario administrador, sin pedir una nueva instalación de WordPress. Esto sucede porque la base de datos (/var/lib/mysql) y los archivos de WordPress (/var/www/html) están almacenados en el host mediante bind mounts (carpetas db y www) y no dentro de los contenedores, por lo que eliminar los contenedores no borra la información.



