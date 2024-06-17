# Prácticas con Dockerfile. Crear una imagen con la base de datos PostgreSQL 16 en un Ubuntu.
## Crear un directorio llamado postgres_imagen. Dentro creamos el archivo Dockerfile.
```
mkdir postgres_imagen
touch Dockerfile
```

## El dockerfile tiene que realizar los siguientes pasos:
1- Descargar la imagen de Ubuntu y actualizar.
```
FROM ubuntu
RUN apt-get update
```
2- Instalamos Postgres
```
RUN apt-get -y install postgresql-16
```
3- Cambiar al usuario postgres y crear el usuario "pguser" con pass "secret" y una base de datos "pgdb".
```
USER postgres
RUN service postgresql start && psql --command "CREATE USER pguser WITH SUPERUSER PASSWORD 'secret';"  && createdb -O pguser pgdb && service postgresql stop
```
4- Volver al usuario ROOT y permitir que cualquier cliente pueda acceder a postgres y por cualquier IP.
```
USER root
RUN echo "host all all 0.0.0.0/0 md5" >> /etc/postgresql/16/main/pg_hba.conf
RUN echo "listen_addresses='*'" >> /etc/postgresql/16/main/postgresql.conf
```
5- Exponer el puerto de la Base.
```
EXPOSE 5432
```
6- Crear un directorio en /var/run y le damos permisos para el usuario postgres.
```
RUN mkdir -p /var/run/postgresql && chown -R postgres /var/run/postgresql
```
7- Crear los volúmenes necesarios para guardar el backup de la configuración, logs y bases de datos y poder acceder desde fuera del contenedor
```
VOLUME ["/etc/postgresql", "/var/log/postgresql", "/var/lib/postgresql"]
```
8- Cmbiar al usuario postgres y arrancar postgres con la configuración adecuada.
```
USER postgres
CMD ["/usr/lib/postgresql/16/bin/postgres", "-D", "/var/lib/postgresql/16/main", "-c", "config_file=/etc/postgresql/16/main/postgresql.conf"]
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/44b9c3f6-c0df-472a-bf79-628db35ccc83)

## Creamos una red llamada red1.
```
docker network create red1
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/659364bd-7223-496e-931d-6cef62a9e149)

## Creamos la imagen con la etiquieta v1 y luego creamos un contenedor y la asociamos a la red1.
```
docker build -t julianzanetti/postgres:v1 .
docker run -d --name postgres2 --network red1 julianzanetti/postgres:v1
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/b3e340ee-fcfd-4e3d-80a4-870c333d45f8)
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/5c91a9ac-9ad4-4706-b78c-5e5a6a9c9a9b)

## Creamos otro contenedor y la asociamos a la red1.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/7533816e-46b6-45a6-96cd-e4a7575e3f59)

## Conectarnos desde el contenedor postgres2 al postgres1. Listar las bases de datos.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/27e99236-2a21-4c70-a0ac-828e86c0c3c9)
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/e137e754-b6cc-4560-92d5-cc687d0f51f5)

## Salir y borrar los contenedores.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/6523609e-cdf0-479f-8270-97dcda29aa05)
