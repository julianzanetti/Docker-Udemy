# Bind Mounts. Crear un directorio compartido entre la máquina principal y el host.
## Descargar la imagen de apache.
```
docker pull httpd
docker images | grep httpd
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/e1d49388-2ea5-45a5-9841-b0646c5d480c)

## Creamos un directorio /app, descomprimimos alguna web que tengamos en ese directorio.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/564c8ab2-a912-41e1-a4ab-e55cede2ccfa)

## Crear un contenedor apache y asociar la ruta del directorio /app a nuestro contenedor apache en la ruta /usr/local/apache2/htdocs/.
```
docker run -d --name apache1 -v /home/Docker/app:/usr/local/apache2/htdocs/ -p 8080:80 httpd
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/9a899602-874d-4bfa-a278-65a17f6ba6be)

## Verificar en el navegador si aparece nuestra pag web.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/a5b6074e-4a15-4b5a-b15c-fce530688859)

## Modificar el fichero index.html desde el host y verificar la web nuevamente.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/aec9e17c-3579-4868-bd9b-f9f63fb35415)

![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/58563624-27ac-4b54-aca2-bc47b2f1ced3)
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/0eebaf3e-0ac4-4610-b4dc-eeb5b813c02c)

## Verificar el tipo de volumen vinculado al contenedor apache.
```
docker inspect apache1 --format '{{json .Mounts}}' | jq
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/56da3e09-e6e3-45e5-8967-b634aa9c74e1)

## Arrancar otro contenedor apache y vincular ese volumen. Verificar desde la web.
```
docker run -d --name apache2 -v /home/Docker/app:/usr/local/apache2/htdocs/ -p 8081:80 httpd
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/43d8687a-7472-4643-a2ce-c1992344afea)
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/370917b4-d024-4968-be3d-5ad41d7765f2)

## Eliminar los contenedores.
```
docker stop apache1 apache2
docker rmm apache1 apache2
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/fd9a8dff-2447-41f9-9a8b-a2718f398553)

