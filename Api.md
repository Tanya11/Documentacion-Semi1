# archivos para la creacion de la imagen de la api que consume la bd

# CREACION DE API CON NODE JS EN DOCKER

Pasos a seguir 

1.Crear un carpeta 
        
                $mkdir api
        
2. Crear ambiente de desarrollo en node js con el comando

                $docker pull node 

3. correr el contenedor

		$docker run -it -v : --name -p : node bash cada una de las letras a poner 
	
significa: -it agregar un script de consola al iniciar el contenedor -v crear un carpeta compartida -d correr el contenedor en segundo plano -p mapear puerto -e agregar variable de entorno --rm borrar el contenedor despues de matarlo ejemplo

		$ docker run -it -v ~/Escritorio/API:/App --name api-node -p 3000:3000 node bash

Ver en que ip se esta coriendo el conteiner 

		$docker inspect --format '{{ .NetworkSettings.IPAddress }}' ${CID} -${CID} 
		
los primeros 4 caracteres que tira el conteiner creado para matar el conteiner ejecutar el siguiente comando 

		$docker kill

Ingresar a la caarpeta app 

		$cd App

Iniciamos el contenedor 

		$npm init

agregar el script start a nuestro archivo json 
			
		{ "name": "app", "version": "1.0.0", "description": "", "main": "index.js", "scripts":
		{ "test": "echo "Error: no test specified" && exit 1", "start": "node index.js" }, 
		"author": "susel", "license": "ISC" }
		

creamos un archivo index.js y agregamos un saludo y luego lo ejecutamos 

		console.log("hola que estes bien");

instalamos express 

		$npm i express

al archivo index agregamos lo siguiente para crear nuestra primera api 

	const express = require('express') const app = express() const ip = process.env.IP || "0.0.0.0" const port = process.env.IP || 		3000 bodyParser = require('body-parser').json();

	app.get('/', function (req, res) { res.send('Hello World' ) })

	app.get('/par',bodyParser, function (req, res) { res.send(req.body); console.log(req.body); }) app.listen(port)

	console.log(se escucha en el puerto ${port} );

# CONEXION DE API CON BASE DE DATOS

semi1bd
# Express.js usando MySQL DB

Herramientas: 

Editor de texto:Visual Studio Code Node.js

Instalación: https://nodejs.org/en/download/ Creando la primera API de Node.js (Express):

# Crea una carpeta para la aplicacion

	$ mkdir aplicacion 
En el terminal / línea de comandos, vaya a la carpeta creada en el paso anterior

	$ cd aplicacion 

Inicializar proyecto de nodo: 
		
	$ npm init 
Para evitar el uso de banderas de preguntas; 

	$ npm init –yes 

Install Express framework, mySql y body-parser 

	$ npm install express –save 
(Express Framework) 
	
	$ npm install mysql –save 
(para conectarse a la base de datos)
	
	$ npm install body-parser 
	
o Este es un middleware node.js para el manejo de datos de formato JSON, Raw, Text y URL codificados.

Configuración del servidor: nodemon nos ayudará a realizar un seguimiento de los cambios en nuestra aplicación al ver los archivos modificados y reiniciar automáticamente el servidor.

	$ npm install --save-dev nodemon Crear un archivo server.js

	$ touch server.js Abrir el archivo server.js 
	
y escribir el código a continuación: 

		var express = require ('express'), app = express (), port = process.env.PORT || 3000; app.listen (puerto);

		console.log ('el servidor de la API RESTful de la lista en:' + puerto);

esto ejecutará su aplicación en el puerto que proporcionó cuando inicia el servidor

																:3
