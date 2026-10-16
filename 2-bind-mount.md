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
```
docker run -d --name svr1 -p 8080:80 -v C:\Users\P3E010-D\Downloads\nginx\html:/usr/share/nginx/html nginx:alpine
```

### ¿Qué sucede al ingresar al servidor de nginx?
Al entrar a http://localhost:8080 aparece el error 403 Forbidden. La carpeta html del host está vacía y no encuentra ningún index.html que mostrar.

### ¿Qué pasa con el archivo index.html del contenedor?
El archivo index.html original del contenedor no se elimina, pero queda oculto por el bind mount. Mientras el montaje esté activo, el contenedor solo accede al contenido de la carpeta del computador, por lo que el archivo original no es visible ni accesible.

### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de tu computador en la carpeta html
### ¿Qué sucede al ingresar al servidor de nginx?
Al ingresar a http://localhost:8080 se muestra el sitio web del template descargado. Los cambios se reflejan sin reiniciar el contenedor, solo recargando la página.

### Eliminar el contenedor
```
docker rm -f svr1
```

### ¿Qué sucede al crear nuevamente un contenedor montado al directorio definidos anteriormente?
Al crear nuevamente el contenedor con el mismo bind mount, se muestra el mismo sitio web del template, sin perder ningún archivo.


