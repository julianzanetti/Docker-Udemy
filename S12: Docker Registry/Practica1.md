## Crear un registro, subir y descargar una imagen.
## Creamos el contenedor con la imagen registry.
```
docker run -d -p 5000:5000 --restart always --name registry registry:2
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/9aaf6010-cae2-46df-9f2e-a9fa00d8dcc5)

## Creamos otro pero este registro seria dedicado solamente a "desarrollo".
```
docker run -d -p 5001:5000 --restart always --name registro-desa registry:2
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/53853be1-68c0-49f1-83c2-37596708fe4c)

## Vamos a subir alguna imagen que tengamos.
```
docker images
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/d74879c0-712b-4dc5-9530-f7a0ca611bca)

```
docker tag mysql localhost:5000/mysql
docker push localhost:5000/mysql
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/ea0910ba-96c6-40a3-ba1e-6171aecda133)

## Verificamos dentro del volumen si se encuentra nuestra imagen.
```
docker inspect registry --format '{{json .Mounts}}' | jq
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/5708e076-e8c2-42d1-b669-d7c937970044)
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/5a2c1f49-b71c-4858-a145-04bcd894a897)

## Verificamos dentro del contenedor.
```
docker exec -it registry sh
cd /var/lib/registry/docker/registry/v2/repositories/
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/a66864cc-fc47-492f-91ee-e60d70addf6e)

## Vamos a descargar la imagen dentro del registro.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/d2f0d61b-242a-4e6d-8345-889329b30bfe)

```
docker pull localhost:5000/mysql
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/03f9fb56-cc2f-4067-afd2-1906ec8f8411)
