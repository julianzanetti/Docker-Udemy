# Caidas de nodos Manager.
## Verificar que nuestra maquina sea un nodo manager.
```
docker node ls
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/89f63192-c6f1-4b4d-8adc-75c8d5e4dfef)

## Para el demonio docker.
```
sudo systemctl stop docker
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/6c993ba0-1aa9-40cb-bf63-57fbe3b063ab)

## Verificar desde otro manager como quedo el cluster.
```
docker node ls
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/6c7e38f6-cbef-4401-95c6-c4955414587f)

Vemos que la instancia que paramos aparece como unreachable y otro manager tomo el mando.

## Arrancar de nuevo el demonio docker y verificar el cluster.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/91723a1f-a510-487d-a43c-6d1baef79658)
