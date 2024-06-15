# Crear volumenes
## Crear un volumen y asignarle el nombre vol1.
```
docker volume create vol1
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/4b4f2865-f7b3-44d4-a4e7-e0d906c497a1)

## Crear un contenedor apache que utilice el volumen vol1
```
docker run -d --name apache1 -v vol1:/usr/local/apache2/htpdocs/ -p 8080:80 httpd
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/30231513-d22a-402e-bbf1-c2473b56376b)

## Comprobar que el contenedor este arriba desde un navegador.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/340953d0-8bb3-426b-b2cf-75354e9bf4d8)

## Dirigirnos a la ruta vol1/_data y editar el archivo index.html. Recargar la pagina.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/b8b646e5-5093-4b69-abba-d541e16a44c4)
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/f9b10415-ee24-4d2a-96ae-5eb0c80080d3)

## Parar el contenedor y borrar el volumen.
```
docker stop apache1
docker rm apache1
docker volume rm vol1
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/47cb3893-0b7a-4d2a-8720-2b52e479cc23)
