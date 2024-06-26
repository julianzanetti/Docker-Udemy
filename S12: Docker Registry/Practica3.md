# Crear un registro privado y securizado.
## Verificar el nombre de nuestra maquina.
```
uname -n
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/f8dc472a-1b46-4b16-80f7-62135382de66)

## Crear una carpeta llamada seguridad dentro del usuario que estamos utilizando (puede ser el root) y dentro descargamos nuestro archivo ssl.
```
mkdir seguridad
openssl req -newkey rsa:4096 -nodes -sha256 -keyout registro.key -x509 -days 365 -out registro.crt  -subj "/CN=DESKTOP-VA3HIEO/C=AR/ST=SFE/L=Rosario/O=Julian/OU=Zanetti" -addext "subjectAltName = DNS:DESKTOP-VA3HIEO"
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/7df94cb2-7ad5-47f8-9379-ba3a2fe0f013)

## Vamos a crear una carpeta con el nombre de nuestra maquina y el puerto 443 en la ruta /etc/docker/certs.d/
```
mkdir -p /etc/docker/certs.d/DESKTOP-VA3HIEO:443
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/3ef0d069-153c-4dd5-a9e7-bb5c77741255)

## Copiar el .crt a la carpeta recien creada.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/60881e85-7f0c-452e-963d-fa1101777e90)

## Generar un archivo de tipo htpasswd con el usuario y contraseña que desees.
```
htpasswd -Bbn usuario contraseña > htpasswd
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/4b9e8a69-051e-4a54-90ad-9e1f90958ee4)

## Creamos la carpeta imagenes_docker que es la que va a almacenar nuestras imagenes (en la ruta que deseemos).
```
mkdir imagenes_docker
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/7876824c-cffa-48d2-91f8-fb60d0fe49f3)

## Generamos el contenedor con las siguientes especificaciones.
```
docker run -d -p 443:443 --restart=always --name registro_privado \
  -v /home/Docker/imagenes_docker:/var/lib/registry \
  -v /home/julianzanetti/seguridad:/auth \
  -e REGISTRY_AUTH=htpasswd \
  -e REGISTRY_AUTH_HTPASSWD_REALM="Mi reino de Seguridad" \
  -e REGISTRY_AUTH_HTPASSWD_PATH=/auth/htpasswd \
  -e REGISTRY_HTTP_ADDR=0.0.0.0:443 \
  -v /home/julianzanetti/seguridad:/certs \
  -e REGISTRY_HTTP_TLS_CERTIFICATE=/certs/registro.crt \
  -e REGISTRY_HTTP_TLS_KEY=/certs/registro.key \
  registry:2
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/42737bbd-b25f-4e73-8931-e0b4647120a7)

## Probamos subir una imagen
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/25b60adc-9de0-43f2-b937-86727359949a)

## Loguearnos y probar subir la imagen nuevamente.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/ab98e130-10d7-4f7b-8bd8-bffa0b9b52da)
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/e40c0031-a71b-4378-8142-bfd8d0239fe2)
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/8fdde9d8-6392-4638-b637-d5b350db4147)

## Si al loguearnos da el error X509, ìr al daemon.json que se encuentra en /etc/docker y agregamos la siguiente linea:
```
"insecure-registries" : ["myregistrydomain.com:5000"]
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/89b75e97-c006-4d22-a78e-9fb6638b26ea)



