# DOCUMENTACIÓN IMAGEN BASE DE DATOS - DOCKER

# Instalación de Docker:
    # sudo apt-get update
    # sudo apt-get install docker.io
    # sudo nano /etc/group
          docker:x:115:ubuntu
# Creación de Imagen
    $ sudo usermod -aG docker $(user)
se utiliza el comando anterior para no tener que correr docker como usuario root, parte de la buena práctica de un desarrollador

Si necesita agregar un usuario al grupo 'Docker' en el que no se ha iniciado sesión, declare explícitamente el nombre del usuario con el siguiente comando:

    $ sudo usermod -aG docker username
    
Crearemos la carpeta del proyecto para la base de datos
    
    $ mkdir db
    
Se creará una carpeta con los scripts de la creación de la base de datos la cual tendra 2 archivos,    
    1. script con create table
    2. script para insertar datos en la tabla.
    
    $ mkdir scripts-sql
    $ nano createTable
          CREATE TABLE product (
            ID varchar(255) NOT NULL,
            name varchar(255) NOT NULL,
            price decimal(10,0) NOT NULL
            PRIMARY KEY (sku)
          );
    $ nano insertTable
          INSERT INTO product (sku,name,price)
          VALUES ('000000','Computadora hp',250000.00);

          INSERT INTO product (sku,name,price)
          VALUES ('000001','Samsung A10',2500.00);

          INSERT INTO product (sku,name,price)
          VALUES ('000002','Huawei p9',1500.00);

          INSERT INTO product (sku,name,price)
          VALUES ('000003','Shampoo',25.00);
          
    $ cd ..

Crear el archivo Dockerfile (archivo con el cual se crea la imagen en Docker)
    
    $ nano Dockerfile
          # Derived from official mysql image (our base image) 
          # esta imagen se descargara de docker revisar que el nombre sea el mismo al igual que la versión :version
          FROM mysql:latest

          # Add a database
          ENV MYSQL_DATABASE nombre_bd

          # Add the content of the sql-scripts/ directory to your image
          # All scripts in docker-entrypoint-initdb.d/ are automatically
          # executed during container startup
          COPY ./archivosSQL/ /docker-entrypoint-initdb.d/


Descargar la imagen de Mysql del repositorio de Docker, imagen que contiene el servidor de mysql para poder utilizarlo, a diferencia de nuestra imagen que contendrá la base de datos por consumir en una api.

    $ docker pull mysql:latest
    
Construir la imagen y el contenedor de nuestra base de datos

    $ docker build -t [nombre de la base de datos] [dockerfile]
    $ docker build -t my-mysql [path carpeta de la bd]
    $ docker build -t my-mysql .
    
Si desea ingresar al contenedor y manipular la bd ejecutar:
     
    $ docker exec -it [nombre de la base de datos] bash
    $ mysql -u root -p
    
Iniciar la base de datos:

    $ docker 
    $ docker run --name some-mysql \
        -e MYSQL_ROOT_PASSWORD=[any pass] \
        -d my-mysql \
        --character-set-server=utf8mb4 \
        --collation-server=utf8mb4_unicode_ci \
        --default-authentication-plugin=mysql_native_password
