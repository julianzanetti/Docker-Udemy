# Practica con apache, nginx, tomcat y mysql.
## Vamos a crear un archivo compose.yml y un archivo mysql.properties.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/f31cbf4c-b317-40d0-ba52-24be1f7f8c2c)

## El compose tiene que contener los servicios nginx, apache y tomcat.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/9eceefd7-1189-4e0c-b13e-e4d989a31fe9)

## Tambien vamos a crear dos servicios de base de datos con la imagen mysql. La primera con las variables dentro del compose y la segunda dentro del archivo mysql.properties.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/9c560c5a-3993-4f4b-83ad-e6fbd1030573)

![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/e1d55d8c-0060-47f9-a176-e20d5f57cfec)

## Levantar el compose y verificar los servicios web.
```
docker compose up -d
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/7e9698cb-38ad-492b-8b9a-9a641fd83de8)

![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/3d7e7153-96e2-400c-8669-e690c1599071)
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/348bf29d-bd6c-4fd8-b42a-793e3b54873b)
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/6d3f6841-9a2c-4239-a4e6-b7e2fdbd909d)

## Verificar la creacion de las bases de datos.
```
docker compose ps
docker compose exec database bash
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/1e36b8f3-05ba-4a12-95d2-654fd1940208)

## Parar todos los servicios creados y eliminarlos. Limpiar completamente docker.
```
docker compose stop 
docker compose ps -a
docker compose rm
docker system prune
docker volume prune
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/f07f4171-1493-4591-936e-bff17603656a)
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/c623a197-b569-40ac-969c-d41843cd6543)
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/19a7a5aa-d1a9-4f96-a4f9-1bbe962c2409)

## Dejamos el .yml completo:
```
services:
  nginx:
    image: nginx
    ports:
      - "80:80"
  apache:
    image: httpd
    ports:
      - "8081:80"
  tomcat:
    image: tomcat
    ports:
      - 8080:8080
  database:
    image: mysql
    environment:
      MYSQL_DATABASE: db1
      MYSQL_USER: usu
      MYSQL_PASSWORD: holamundo
      MYSQL_ROOT_PASSWORD: holamundo
  database2:
    image: mysql
    env_file:
      - mysql.properties
```

## Archivo mysql.properties.
```
MYSQL_DATABASE= db1
MYSQL_USER= usu
MYSQL_PASSWORD= holamundo
MYSQL_ROOT_PASSWORD= holamundo
```
