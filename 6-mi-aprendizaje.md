# COMPLETAR  
Comparando sus conocimientos antes de hacer la práctica con sus conocimientos después de hacer la tarea, explicar los principales aprendizajes logrados para beneficio de su formación profesional.  
Si solucionó un problema presentado o utilizó otros comandos que no se mencionan al realizar la práctica también se debe documentar.
#
**Antes de la práctica:** conocía Docker de forma básica, sabía que los contenedores ejecutan aplicaciones, pero no tenía claro cómo funcionaba todo lo relacionado al tema.

**Después de la práctica:** comprendí que los contenedores son efímeros y que los datos se conservan usando almacenamiento externo, aprendí a: Crear redes, usar bind mounts, usar volúmenes nombrados y anónimos, conectar varios servicios.

**Problema solucionado:** Al hacer el ejercicio de WordPress apareció el error "Error establishing a database connection". La causa fue que renombré el contenedor de MySQL a cont-mysql, pero en WORDPRESS_DB_HOST seguía el nombre anterior (mysql-wp). Lo solucioné así:
```
docker rm -f cont-wordpress
docker run -d --name cont-wordpress ... -e WORDPRESS_DB_HOST=cont-mysql ... wordpress
```
**Beneficio profesional:** Estos conocimientos me permiten desplegar aplicaciones de forma rápida
