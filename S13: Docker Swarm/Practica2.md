# Añadir un nodo worker y un nodo manager al cluster.
## Desde nuestro leader verificamos cual es el token para que se unan a nuestro cluster.
```
docker swarm join-token worker
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/83a7a0cc-3be5-462d-bce9-12dc1229657c)

## Desde otra maquina copiamos el comando que nos muestra y lo ejecutamos.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/707609be-6b7c-4aca-83c6-60dafac6898b)

## Desde el worker podemos listar los nodos?
```
docker node ls
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/4b6e5c56-2cdc-49ce-ba39-2ef789578b07)

## Vamos a agregar otro worker mas.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/6c4b2dc8-7409-4573-af36-396d8b32d957)
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/17f4955d-a744-4cc7-aa3e-7c186691f523)

## Verificamos cuantos nodos tenemos con docker info.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/110f4896-5e9a-4126-8d81-0dee5b245c82)

## Vamos a agregar un nodo de tipo manager.
```
docker swarm join-token manager
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/2762845e-6f8a-4388-8ae2-b16dc8051c1b)

## Probamos listar los nodos en este nuevo manager.
```
docker node ls
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/204319bd-5dea-4060-8d94-aadbaa3c7d88)

## Docker recomienda siempre tener managers impares.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/284b85f8-4e8b-4291-aefc-d7b3b8041fb6)
