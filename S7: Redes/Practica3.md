# Configurar puertos y conectar contenedores.
Vamos a crear dos contenedores de MariaDB, uno como cliente y otro como servidor.

### Descargamos la imagen de mariadb y averiguamos por los puertos que escucha dicha imagen.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/b5e03837-1967-4616-8a6b-f2c645c972f2)

### Creamos un contenedor de nombre mariadb1 que escuche por el puerto 4000. Verficar su estado y puertos.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/9bb537a8-65cc-4034-b635-56d09a8f9f43)
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/55c0a1e0-f6cf-4ac2-832a-14548262bf87)

### Comprobar las redes que tenemos y sus contenedores conectados.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/06928ff4-e849-4e15-ac50-6b55b7092665)
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/6a589998-b5c0-4b24-9e8f-6ede1ada422e)

### Crear un segundo contenedor de nombre mariadb2 que escuche por el puerto 4001. Verficar su estado y puertos.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/409efd40-3f8b-46e6-b31b-e09757c79e3e)

### Comprobar nuevamente la red bridge.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/a0c546b0-c0dc-46d8-b6ea-ebd1d1efdbd0)

### Probar de llegar de un contenedor a otro.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/31785f58-712c-410f-a67e-e58b7d559ffb)

### Conectarse desde mariadb2 a la base de datos de mariadb1.
Primero creamos una base de datos en mariadb1 para diferenciarla de mariadb2.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/2def0e68-f448-4c98-a128-0095cf4aa6d6)

Verificamos que en mariadb2 no existe.

![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/dfc967d2-6802-4a6c-95bd-cd50a63a9b02)

Salimos, realizamos la conexion nuevamente y mostramos.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/7e62ae94-01de-4769-9fb2-43986743ac29)
