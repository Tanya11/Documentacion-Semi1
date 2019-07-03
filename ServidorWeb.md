
# Servidor web con nginx
Contenido de fase 1 del proyecto de seminario de sistemas vacaciones de junio 2019

	Pasos para crear la pagina web

1.apt-get install docker.io 
2.ahora crear una carpeta que sera nuestro proyecto 
	
	$ mkdir paginadocker
3.Ingresar al archivo y colocar lo siguiente 

	$nano Dockerfile Dockerfile
4. al ingresar colocar esot en el dockerfile
		
		FROM ubuntu:18.04 
		RUN apt-get update 
		RUN apt-get install -y nginx 
		WORKDIR /var/www/html 
		RUN rm * 
		COPY index.html . 
		#ADD carpeta /root/ EXPOSE 80 
		#ENV VAR_ENTORNO contenido CMD /usr/sbin/nginx -g "daemon off;"

4.EN la misma carpeta crar el un index.html 
		 
		 $nano index.html

5.poner el siguiente html

	HOLA COMO ESTAN ESTA ES UNA PAGINA WEB

6. O se puede poner simplemente el html de la pagina que se va a utilizar Ssiempre dentro de la carpeta creamos la imagen con el siguiente comando

		$ docker build -t . tanyarecinos/apache2:latest

7.ERROR SI APARECE QUE NOS E PUEDE CREAR ENTONCES AGREGAR EL PUNTO DE ULTIMO DE ESTA FORMA

		$docker build -t tanyarecinos/apache2:latest . 8.Ahora para subir la imagen tenemos que loguearnos

8. Loguearnos a docker hub en la consola

		#docker login

9.Podemos ver que si se creo la imagen dando el comando 

	$docker images 

10.Y corremos el conteiner 
			
	$ sudo docker run -p 8002:80 -d -it tanyarecinos/paginasirve 

11.y ya logueados subimos la imagen a docker hub con:

	$docker push tanyarecinos/apache2:latest

12.despues para hacer la prueba de que sirve podemos descargar la immagen con el comando 

	$docker pull tanyarecinos/apache2:latest 

13.y luego le damos run a la imagen que descargamos
		
	$ docker run -p 8002:80 -d -it tanyarecinos/tagname

13.para ver en que puerto esta corriendo le damos 

	$docker inspect %ID 
	
donde el ID son los primeros 4 caracteres del conteiner que sse crea despues de darle run 

14. Ahora podemos ir al puerto donde esta corriendo la pagina y podemos ver lo que escribimos en el html

					# FIN
