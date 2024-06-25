# Lanzar comandos al levantar los servicios.
## Creamos cuatro archivos: apache.sh, nginx.sh, Dockerfile y docker-compose.yml
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/a8425ce8-90d7-48dc-98f4-2bfa157876ef)

## El Dockerfile tiene debe:
1. Descargar la imagen de ubuntu y actualizar el sistema.
2. Instalar el nginx y el apache
3. Agregar el nginx.sh y el apache.sh al /usr/local/bin/ y darle permiso de ejecucion.
4. Exponer el puerto 80

![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/cfc97aa0-f785-4aeb-ace1-3da71146a61f)

## El archivo apache.sh debe iniciar el apache en primer plano y realizar un echo al index.html.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/d859f056-8af7-441f-a85d-0b69e0432a2a)

## Lo mismo para el archivo nginx.sh.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/7aa8b86b-7b39-4c4c-a2cb-a5a824f0b4c4)

## El compose debe construir la imagen y dependiendo que perfil elija, debe levantar el apache o el nginx.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/8dab2bb1-9968-476a-b7e5-c020995645a3)

## Construimos la imagen y levantamos los dos servicios.
```
docker compose build web-apache
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/55cdbc27-d51c-4f80-97a6-f16102d98430)
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/5fbde156-79a3-4cc0-aa75-70dea082e590)

```
docker compose --profile apache up -d
docker compose --profile nginx up -d
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/097fe7c5-bd2c-4c27-b78a-5f352cad4b2f)
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/7611da92-d1ff-4887-88f5-0d737ddcc2e1)
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/71d6bdd1-a5a7-403d-83a3-1af54e191a09)

## Removemos los dos servicios.
```
docker compose --profile apache down
docker compose --profile nginx down
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/2ccc7560-70db-4889-9a26-c406666ed5be)

## Dejo el compose.yml:
```
services:
  web-apache:
    build: .
    image: comando-web:latest
    container_name: apache
    ports:
      - 8090:80
    command: ["/usr/local/bin/apache.sh"]
    profiles:
      - apache

  web-nginx:
    build: .
    image: comando-web:latest
    container_name: nginx
    ports:
      - 8080:80
    command: ["/usr/local/bin/nginx.sh"]
    profiles:
      - nginx
```

## Dockerfile:
```
FROM ubuntu
RUN apt-get update

#Instalamos el ngnix
RUN apt-get install -y nginx

#Instalamos el apache
RUN apt-get install -y apache2

#Creamos un iniciador para ngnix
ADD nginx.sh /usr/local/bin/
RUN chmod +x /usr/local/bin/nginx.sh

#Creamos un iniciador para apache
ADD apache.sh /usr/local/bin/
RUN chmod +x /usr/local/bin/apache.sh

#Ponemos cualquier cosa en el CMD - No es importante para el ej.
CMD [ "echo", "prueba de comando" ]

#Exponemos el puerto 80
EXPOSE 80
```

## Nginx.sh
```
#!/bin/bash
echo "Estoy en nginx" > /var/www/html/index.html
nginx -g "daemon off;"
```

## Apache.sh
```
#!/bin/bash
echo "Estoy en apache" > /var/www/html/index.html
apachectl -D FOREGROUND
```
