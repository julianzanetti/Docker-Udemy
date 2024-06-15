# Volumen de tipo TMPFS.
## Descargar la imagen de ubuntu y crear un contenedor.
```
docker pull ubuntu
docker images | grep ubuntu
docker run -d -it --name ubuntu1 ubuntu
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/86fd2567-1ce6-4fb2-807a-8a72240a82a3)
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/ca56df3b-b723-404f-91b6-4fda9fb0bc9e)

## Entrar al contenedor ubuntu, y crear un archivo en el directorio /home.
```
docker exec -it ubuntu1 bash
cd /home/
touch archivo.txt
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/e805825e-da38-4822-be3d-910d0a1f25ee)

## Parar el contenedor, volver a arrancar y verificar que siga existiendo el archivo.
```
docker stop ubuntu1
docker ps -a
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/c33e4370-8984-4129-ab08-ba92f65ab518)

```
docker start ubuntu1
docker exec -it ubuntu1 bash
cd /home/
ls
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/30f60d6d-af51-4848-8b8d-e19e4d315f59)

## Ahora crear otro contenedor ubuntu y asociar un volumen de tipo tmpfs en el directorio /datos.
```
docker run -d -it --name ubuntu2 --tmpfs /datos ubuntu
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/2ef5a3bf-a16c-4776-ba0f-3d704b9fcbb9)

```
docker exec -it ubuntu2 bash
cd /datos/
touch borrar.txt
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/27d16cbc-c252-4d3e-bfa5-07e27a5a090e)

## Parar y volver a arrancar el contenedor, verificar el directorio /datos.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/c96cddf9-dc73-471e-b6d6-b790ae4dc011)
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/861f0c85-edfa-4636-9e2a-653b9b4cdd92)
