# DespliegueProyecto

## Objetivos

Los objetivos de esta práctica son realizar un despliegue de nuestra aplicación mediante docker compose. Además de crear una imagen personalizada de nuestro proyecto y subirlo a nuestro docker hub para que después se pueda hacer un pull de nuestra imagen y ejecutarla en cualquier equipo.

## Paso 1

En primer lugar, exportaremos nuestro proyecto en un fichero .war y lo guardaremos en una nueva carpeta. Para ello, en Eclipse, hacemos click derecho sobre nuestro proyecto, seleccionamos la opcion "Export" y seguidamente la opcion "WAR File".
![1]()

## Paso 2

En Visual Studio, abriremos nuestra carpeta y crearemos un nuevo fichero DockerFile, que guardaremos en la misma carpeta.
![2]()

## Paso 3 - DockerFile

Una vez creado nuestro DockerFile, procedemos a completarlo indicando los siguientes campos:
1. FROM <imagen base>:latest
2. LABEL maintainer="<Nombre del creador>"
3. COPY <ruta del archivo local .war> /usr/local/tomcat/webapps/
4. EXPOSE 8080
5. CMD ["catalina.sh", "run"]

Por tanto, nos quedaria un DockerFile con la siguiente información:

![3]()
  
Seguidamente, hacemos un build de nuestra imagen personalizada. Para ello hacemos click derecho y hacemos click en la opción "Build Image". 
![4]()  
Acto seguido, indicamos el nombre de nuestra imagen personalizada y aceptamos.
![5]()
Finalmente, en consola se nos indica que todo ha ido correctamente.
![6]()
  
## Paso 4 -- Docker Compose
  
  
