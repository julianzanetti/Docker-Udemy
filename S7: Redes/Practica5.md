# Enlazar contenedores.
### Vamos a crear un contenedor mysql llamado mysql_server, con las variables ={usuario=wp y una contraseña, una contraseña al usuario root, una BD=wpdb y asignar el puerto 3100}, este contenedor lo asignaremos a la red1 creada en la practica anterior.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/04485e62-5c81-4d12-896e-e34c6ef39c05)

### Verificamos que la base wpdb se haya creado correctamente.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/1f8511d6-926f-441c-a5b2-688ca1a39ba7)

### Creamos un contenedor wordpress llamado wp1 y las variables = {host=mysql_server, nombredb=wpdb, usuario=wp una contraseña, asignar el puerto 9000}, tambien lo asignamos a la red1.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/0eea7ddd-2535-4515-b9c3-2985eda6002e)

### Verificamos los contenedores conectados a la red1.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/1a4e92f6-a353-480c-86c7-dfe7ebbc10f2)

### Realizar la instalacion del wordpress.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/63927660-6736-4d56-8326-0c2da4389a0f)

### Conectarnos a la base de datos wpdb en mysql_server con el usuario wp y verificar las tablas que creo wordpress.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/1ef873ba-4ec2-4515-93b7-45f6ac778cb5)
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/675b8159-4047-47bd-9a24-3809ecaf54ea)
