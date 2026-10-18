## Esquema para el ejercicio
![Imagen](esquema-ejercicio3.PNG)

### Crear red net-wp
```
docker network create net-wp
```

### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio carpeta del contenedor (a) es (__/var/lib/mysql__)

Ruta carpeta host:
```
C:\docker\ejercicio3\db
```

### ¿Qué contiene la carpeta db del host?
Al inicio está vacía, porque todavía no se ha creado ningún contenedor.

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
```
docker run -d --name cont-mysql --network net-wp -v C:\docker\ejercicio3\db:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=rootpass -e MYSQL_DATABASE=wordpress -e MYSQL_USER=wpuser -e MYSQL_PASSWORD=admin mysql:8
```

### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
Se llenó con los archivos de datos de MySQL

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio la carpeta del contenedor (b) es (__/var/www/html/__)

Ruta carpeta host:
```
C:/docker/ejercicio3/www
```

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
```
docker run -d --name cont-wordpress --network net-wp -p 9500:80 -v C:\docker\ejercicio3\www:/var/www/html -e WORDPRESS_DB_HOST=cont-mysql -e WORDPRESS_DB_USER=wpuser -e WORDPRESS_DB_PASSWORD=admin -e WORDPRESS_DB_NAME=wordpress wordpress
```

### Personalizar la apariencia de wordpress y agregar una entrada
<img width="1875" height="969" alt="image" src="https://github.com/user-attachments/assets/76bd1e1a-a36f-480f-bdd7-3a6f3fc4fc41" />

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?
El sitio aparece igual que antes, con el tema personalizado y la entrada publicada, sin volver a pedir la instalación.
