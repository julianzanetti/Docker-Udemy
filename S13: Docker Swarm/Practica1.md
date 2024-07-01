# Crear un cluster Swarm.
## Requisitos.
1. Tener varias maquinas (fisicas o virtuasles).
2. Docker debe estar corriendo en todas estas maquinas.
3. En mi caso voy a utilizar maquinas de AWS.

## Verificamos nuestra IP.
```
ifconfig
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/1a534248-e40f-4c3e-94d4-a53a4faee2b2)

## Vamos a crear nuestro primer nodo de tipo leader.
```
docker swarm init --advertise-addr ip-del-servidor
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/62ad65f8-86ba-4be1-9379-90cafb42dcc7)

## Verificamos que quedo activo.
```
docker info
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/062cf6f3-bc23-4f7d-8334-d3232593fca1)

## Listamos nuestros nodos.
```
docker node ls
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/c982f5e4-75cb-47fa-8b46-f08b5efd39b8)
