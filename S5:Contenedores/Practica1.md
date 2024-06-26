# Visualizar nuestros primeros contenedores
### 1- Vamos a crear nuestro primero contenedor usando la imagen de hello-world.
```
docker run hello-word
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/818c78dc-0e27-48af-83ff-8aa9b66ab49a)

### 2- Comprobamos el estado del contenedor creado.
```
docker ps -a
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/a437ae7b-3817-482b-869e-91dbefb0abcd)

### 3- Comprobamos que la imagen exista.
```
docker images
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/9bf8870a-5e09-4b89-89c3-c9aedb94cb10)

### 4- Creamos un nuevo contenedor con la imagen busybox de DockerHub.
```
docker run busybox
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/5a2bee1f-b69c-4215-bda3-d90df6774ab6)

### 5- Comprobamos que exista la imagen busybox.
```
docker images | grep busy
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/b7fafd33-4a8b-4a04-a133-21c03a0aadba)

### 6- Visualizar solo los ID de los contenedores.
```
docker ps -aq
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/9bb15126-2887-4fe9-bb19-2d737b0be137)

### 7- Ver los ultimos dos contenedores lanzados.
```
docker ps -a -n 2
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/746e7a55-de67-4469-bb51-639ceaeba5dc)

### 8- Comprobar el espacio utilizado por los contenedores creados.
```
docker ps -a -s
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/a85bea2a-149c-42d6-bb33-043454072a74)
