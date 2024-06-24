# Contextos. Trabajar con varios entornos.
## Listar los diferentes contextos.
```
docker context ls
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/b119d65d-06ca-44cc-b0e9-685dd7d3ee36)

## Crear un conexto con el demonio creado en la practica anterior.
```
docker context create docker-desa --docker host=unix:///var/run/docker-desa.sock
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/c238dc92-2231-4851-a3cb-46f8dbb0348c)
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/cb190ccc-0877-4a13-8dab-8b480fed0485)

## Elegir el nuevo contexto para utilizarlo.
```
docker context use docker-desa
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/03cdd5bf-57ad-4b54-85fe-203011d33e08)

## Verificar que estemos con el nuevo demonio.
```
docker info
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/e26d6859-e70e-423f-a738-74d03c612cd1)

## Volver a la configuracion anterior.
```
docker context use default
```
