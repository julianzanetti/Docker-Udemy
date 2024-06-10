# Crear Redes y asociarlas a contenedores.
### Comprobar las redes que tenemos por el momento.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/ecbcd0a5-abcf-4817-8297-58e8e62517e1)

### Crear una nueva red de tipo bridge con el nombre red1.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/7656e6ad-4e28-4c6b-a853-443ad959643e)

### Inspeccionar la red1.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/24be2684-42cb-4f84-a096-76d36f90dd64)

### Creamos un contenedor apache1 con esa red. Comprobamos que levante correctamente.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/c4a1c606-b5cf-4f3e-a4bd-23ccea04459d)

### Comprobar en la red que el contenedor apache se haya unido correctamente.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/d4909c72-f643-480e-a2e4-b019ee79d2e1)

### Crear otro contenedor apache2, entrar dentro y realizar un ping al contenedor anterior.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/fdd146aa-93e7-40e7-bf04-5195601d41ce)
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/3fe498f4-cf66-4140-8821-d466883ef124)

### Crear otra red de tipo bridge con nombre red2, que su subred sea la 172.30.0.0/16 y que los contenedores asociados comiencen con una IP a partir de la 172.30.10.0/24.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/d7e64a88-dd00-4ad3-8e67-9f0f041ff3d5)

### Comprobar que los datos ingresados en la red esten correctos.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/6baf30f8-5b65-4a8b-b0d4-a4fb6d028477)

### Crear un tercer contenedor apache3 y lo conectamos a la red2. Comprobar dicha conexion.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/a3a06b15-c3e8-4c84-bc1f-96e5dc7f42b1)
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/60e5e271-837f-464a-93f8-21f2f8b79552)

### Probar realizar un ping desde el apache1 al apache3.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/ccee999b-f8c0-47cd-96fa-cdc163c88186)

### Asociar la red1 al apache3. Verificar las conexiones que tiene el contenedor.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/80352828-43fb-4648-9976-fde25ca64d06)

### Verificar los contenedores conectados a la red1 y la red2.
red1:

![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/53c91447-6c3d-4ae2-af08-ec3ce3b2e952)

red2:

![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/881251ba-c767-4e29-93a8-c5369156ca11)

### Volver a probar realizar un ping desde el apache1 al apache3.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/3bde7275-a49d-4891-8860-ef4d3b3d42d6)

### Desconectar el apache3 de la red1. Verificar la desconexion.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/3aedca53-edb2-4f12-a7f6-5cac7294b966)
