# DespliegueProyecto

## Objetivos

Los objetivos de esta práctica son realizar un despliegue de nuestra aplicación mediante docker compose. Además de crear una imagen personalizada de nuestro proyecto y subirlo a nuestro docker hub para que después se pueda hacer un pull de nuestra imagen y ejecutarla en cualquier equipo.

## Paso 1

En primer lugar, exportaremos nuestro proyecto en un fichero .war y lo guardaremos en una nueva carpeta. Para ello, en Eclipse, hacemos click derecho sobre nuestro proyecto, seleccionamos la opcion "Export" y seguidamente la opcion "WAR File".
![1](https://github.com/cosmetorandellborras/DespliegueProyecto/blob/main/1.png)

## Paso 2

En Visual Studio, abriremos nuestra carpeta y crearemos un nuevo fichero DockerFile, que guardaremos en la misma carpeta.
![2](https://github.com/cosmetorandellborras/DespliegueProyecto/blob/main/2.png)

## Paso 3 - DockerFile

Una vez creado nuestro DockerFile, procedemos a completarlo indicando los siguientes campos:
1. FROM <imagen base>:latest
2. LABEL maintainer="<Nombre del creador>"
3. COPY <ruta del archivo local .war> /usr/local/tomcat/webapps/
4. EXPOSE 8080
5. CMD ["catalina.sh", "run"]

Por tanto, nos quedaria un DockerFile con la siguiente información:

![3](https://github.com/cosmetorandellborras/DespliegueProyecto/blob/main/3.png)
  
Seguidamente, hacemos un build de nuestra imagen personalizada. Para ello hacemos click derecho y hacemos click en la opción "Build Image". 
![4](https://github.com/cosmetorandellborras/DespliegueProyecto/blob/main/4.png)  
Acto seguido, indicamos el nombre de nuestra imagen personalizada y aceptamos.
![5](https://github.com/cosmetorandellborras/DespliegueProyecto/blob/main/5.png)
Finalmente, en consola se nos indica que todo ha ido correctamente.
![6](https://github.com/cosmetorandellborras/DespliegueProyecto/blob/main/6.png)
  
## Paso 4 - Docker Compose

Con el fin de levantar todos los servicios que componen nuestra aplicación, crearemos un fichero docker-compose.yml que guardaremos en la misma carpeta.
Una vez creado nuestro docker-compose.yml, procedemos a completarlo indicando los siguientes campos:

1. version: 'x' / Indicamos la versión del documento
2. services: 
3. web: / Indicamos el tipo de servicio
4. image: / Indicamos la imagen
5. ports: / Indicamos el redireccionamiento de puertos
6. volumes: / Indicamos los volumenes de la imagen
  
Además, se pueden ir añadiendo los diferentes tipos de servicios que arrancaran cuando arranquemos nuestro docker-compose y que relación tendrán entre los servicios.
  
Por tanto, nos quedaria un fichero docker-compose.yml con la siguiente información:
  
![7](https://github.com/cosmetorandellborras/DespliegueProyecto/blob/main/7.png)
  
Seguidamente, para arrancar los contenedores, hacemos click derecho y seleccionamos la opción "Compose Up"
![8](https://github.com/cosmetorandellborras/DespliegueProyecto/blob/main/8.png)
  
Una vez arrancado, podemos ir a nuestro navegador e indicar la siguiente direción para comprobar que ha arrancado correctamente y podemos ver nuestro proyecto
~~~
localhost:8081/ProjecteFinal
~~~
![9](https://github.com/cosmetorandellborras/DespliegueProyecto/blob/main/9.png)
  
## Paso 5 - Subir imagen a Docker Hub
En primer lugar, vamos a nuestra extensión de Docker en Visual Studio, y nos logueamos a Docker Hub con nuestra cuenta.
Después seleccionamos nuestra imagen, hacemos click derecho sobre ella y seleccionamos la opción "Push", indicamos la cuenta donde haremos el push y el nombre que le daremos.
![10](https://github.com/cosmetorandellborras/DespliegueProyecto/blob/main/10.png)
Esto sube la imagen personalizada a mi cuenta de docker hub.
  
## Paso 6 - Docker Hub
  
Ahora comprobamos que el proceso ha concluido correctamente, vamos a nuestro usuario de Docker Hub y comprobamos que aparece nuestro contenedor personalizado
  
![11](https://github.com/cosmetorandellborras/DespliegueProyecto/blob/main/11.png)
 
[dockerhub trui20/servicioshogar](https://hub.docker.com/r/trui20/servicioshogar)
  
Podemos hacer un docker pull del contenedor y ejecutarlo en cualquier equipo
  
  
  
  
