# Servicios Globales.
## Crear un servicio global.
```
docker service create --name web3 -p 8081:80 --mode global nginx
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/ae6c3818-4fe6-494e-b225-de3955697547)
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/88c3c148-eac6-4889-9df8-9b7339902f47)

## Agregar un nuevo nodo a nuestro cluster y verificamos el servicio nuevamente.
```
docker swarm join-token worker
docker service ls
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/220d84ab-2e95-4b89-ae5e-6a7a32d7be3d)
