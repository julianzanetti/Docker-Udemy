# Promover/Degradar nodos.
## Vamos a promover un worker a manager.
```
docker node ls
docker node promote id-nodo
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/8d86f251-653a-4e91-a4bb-b6bcc8936204)

## Verificamos ahora desde la maquina que promovimos.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/cd9ba5eb-c12b-453d-a54d-75c3209ac080)

## Vamos a degradar un manager a worker.
```
docker node ls
docker node demote id-nodo
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/9e82c966-604f-437e-a7da-2454120dbb13)

## Verificamos nuestro cluster nuevamente.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/ca756cd2-5eae-4fea-912f-25b06bd58db9)
