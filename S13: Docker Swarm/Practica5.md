# Crear y acceder a un servicio.
## Vamos a crear un servicio basado en la imagen de apache.
```
docker service create imagen
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/d232054e-24f6-4ac7-8633-428d98dbc237)

## Listamos nuestros servicios y vemos en que nodo lo creo.
```
docker service ls
docker service ps apache
docker node ls
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/9519f823-ae7b-4ddc-a54e-8ee462560ca2)

## Inspeccionamos el servicio.
```
docker service inspect apache --pretty
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/2743eb48-19e4-4e01-8ead-72a7256c835c)

## Vamos a crear otro servicio con la imagen de apache pero que este sea accesible.
```
docker service create --name apache-web --publish published=9000,target=80 httpd
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/df4fd3da-ec04-4ca8-a69c-409b81a03767)

## Listamos y verificamos nuestro servicios.
```
docker service ls
docker service ps apache
docker node ls
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/d1a3e302-d1c3-48c6-bacd-a0137919f2ef)

## Accedemos a nuestro servicio desde el nodo del cluster.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/9ace63c6-834e-49af-b24c-dccf8c769b63)
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/4864faf2-6ab8-48bc-884f-91cfc567836f)
