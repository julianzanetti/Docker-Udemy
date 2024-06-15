# Prácticas con Dockerfile. Creación de un ejemplo con Nginx.
## Crear un directorio denominado imagen_nginx. Dentro creamos el archivo Dockerfile.
```
mkdir imagen_nginx
touch Dockerfile
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/4092614f-e25e-40ed-9d48-ea85a7cd1cd1)

## El dockerfile tiene que realizar los siguientes pasos:
1- Descargar la imagen de ubuntu.
```
FROM ubuntu
```
2- Actualizar el sistema.
```
RUN apt-get update
```
3- Instalar nginx.
```
RUN apt-get install -y nginx
```
4- Crear un archivo index.html en el directorio por defecto de nginx.
```
RUN echo 'Mi primer Dockerfile' > /var/www/html/index.html
```
5- Arrancar nginx.
```
RUN echo 'Mi primer Dockerfile' > /var/www/html/index.html
```
6- Exponer el puerto 80.
```
EXPOSE 80
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/6bb30c4d-9ff5-40c8-95a9-6d2b29920a0a)

## Crear la imagen con su usuario de Docker Hub.
```
docker build -t julianzanetti/ngnix:v1 .
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/980ba566-86e0-4a31-945e-0fb550f99fd8)

## Arrancar un contenedor con esa imagen, verificar desde la web.
```
docker run -d --name ngnix1 -p 8080:80 --rm julianzanetti/ngnix:v1
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/70b4acd3-384d-41e1-a154-654200b831a5)
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/de3c4da7-21b4-4752-86d3-f6565be63730)

## Descargar una web desechable, crear un directorio web en la ruta del Dockerfile y descomprimir la web desechable.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/600c1bfb-21ad-4fd0-bddd-7a435c16251b)

## Modificar el Dockerfile para que pase el contenido del la carpeta web a la ruta /var/www/html/. Crear una nueva imagen con el tag v1.
```
ADD web /var/www/html/
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/f62bd9d5-08d5-4157-8b3a-5972011aa4f1)

```
docker build -t julianzanetti/nginx:v1 .
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/ac1b0dc4-ad4b-40a7-9afb-d0038c78d6e4)

## Crear otro contenedor con esa imagen y verificar en la web.
```
docker run -d --name nginx2 -p 8081:80 --rm julianzanetti/nginx:v1
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/33735160-cc86-4bea-b710-0e3e956ed856)
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/0531d190-c66f-4ab9-ae4c-8649bdc06417)

## Asignar un volumen a la imagen desde el Dockerfile. Crear otra imagen con el tag v2.
```
VOLUME /var/www/html/
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/8c678999-b2c7-42a3-a0a0-611ea68c8142)
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/5da1fdd7-4245-4b1f-9d08-45c76b961784)

## Crear un contenedor nuevo con esta imagen. Verificar si se creo el volumen.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/e624fc4a-4215-4b22-8f0b-8bf18a8a2653)

## Modificar desde el /_data el archivo index.html. Verificar desde la web.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/10197266-3626-4b8a-88e5-84143da6425d)

## Creamos un directorio web2 en la ruta del Dockerfile. Descomprimir otra web desechable.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/baf003b6-2d81-43d6-97cb-c2a3bc22721e)

## Modificar el Dockerfile para que podamos elegir que web desplegar pasando como parametro el directorio.
```
ARG webpage
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/c38476a1-b877-4066-a307-5996a0f94a80)

## Crear otra imagen con el tag v3. Desplegar la web2.
```
docker build -t julianzanetti/nginx:v3 --build-arg webpage=web2 .
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/90faf144-b68b-4d29-a6c4-8853e9aa1940)

## Levantar un contenedor con esta imagen.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/b7887fe8-6392-439d-a07e-a3bb941677e7)
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/aa65b9e9-c920-43ed-a3ac-1fdb21125b98)

## Repetir los pasos anteriores pero desplegando la web.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/e74f2635-64a8-4292-afc8-51fe80da47a5)
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/af2ca1d9-4ed5-411e-aa83-a15b34023af8)
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/2a525174-cfd5-4f03-8fac-83b37b4f9339)
