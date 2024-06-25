## Practica con wordpress y mysql.
## Crear el servicio de db-wp con la imagen mysql, sus respectivas variables y un volumen llamado db-desa (Este servicio seria de desarrollo).
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/05466225-35d5-40e7-95e8-f4952bc838b1)

## Crear el servicio de db-wp-produ con la imagen mysql, sus respectivas variables y un volumen llamado db-produ (Este servicio seria de produccion).
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/abc65aeb-941c-474a-939e-412bcc13608f)

## Crear el servicio de wordpress, en el puerto 9090 con sus respectivas variables, en la red front, los perfiles desarrollo y produccion y con un volumen llamado wp.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/7f202396-10e8-4d5d-8fae-69ed771bbf22)

## Asi quedaria el docker-compose.yml:
```
services:
  wordpress:
    image: wordpress
    container_name: wordpress
    restart: always
    ports:
      - 9090:80
    environment:
      WORDPRESS_DB_HOST: db-host
      WORDPRESS_DB_USER: wp-user 
      WORDPRESS_DB_PASSWORD: holamundo
      WORDPRESS_DB_NAME: wp-db 
    #depends_on:#
      #- db-wp#
    volumes:
      - wp:/var/www/html
    networks:
      - front
    profiles:
      - desarrollo
      - produccion
  
  ##BBDD DESARROLLO##
  db-wp:
    image: mysql
    container_name: desarrollo-bd
    restart: always
    environment:
      MYSQL_DATABASE: wp-db
      MYSQL_USER: wp-user
      MYSQL_PASSWORD: holamundo
      MYSQL_ROOT_PASSWORD: holamundo 
    volumes:
      - db-desa:/var/lib/mysql
    networks:
      front:
        aliases:
          - db-host
    profiles:
      - desarrollo

  ##BBDD PRODUCCION##
  db-wp-produ:
    image: mysql
    container_name: produccion-bd
    restart: always
    environment:
      MYSQL_DATABASE: wp-db
      MYSQL_USER: wp-user
      MYSQL_PASSWORD: holamundo
      MYSQL_ROOT_PASSWORD: holamundo 
    volumes:
      - db-produ:/var/lib/mysql
    networks:
      front:
        aliases:
          - db-host
    profiles:
      - produccion

volumes:
  wp:
  db-desa:
  db-produ:

networks:
  front:
```

## Probamos levantar solamente el entorno de desarrollo.
```
docker compose --profile desarrollo up -d
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/fa7bf284-1b02-4616-a760-dfc47ffc449e)

## Removemos el servicio de desarrollo y levantamos el de produccion.
```
docker compose --profile desarrollo down
docker compose --profile produccion up -d
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/3c19502d-d40f-46a9-8d82-5db309e45d8a)

