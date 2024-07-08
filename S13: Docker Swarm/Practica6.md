# Replicas en los servicios.
## Crear un servicio con un nro de replicas especifico.
```
docker service create --name web1 -p 8003:80 --replicas=2 httpd
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/24f76247-fab8-4832-b2c0-69273ff5c216)

## Subir nro de replicas.
```
docker service scale web1=3
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/f5e76eca-4505-4060-a5b2-0ab70cdf0b16)

## Bajar nro de replicas.
```
docker service scale web1=2
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/2db5e0e8-76d7-4741-a076-2be1ffe022e2)
