# Crear otro demonio dockerd.
## Creamos los directorios necesarios.
```
sudo mkdir -p /var/lib/docker-desa /var/run/docker-desa
```

## Creamos un ejecutable .sh con los siguientes argumentos:
```
sudo dockerd \
    -H unix:///var/run/docker-desa.sock \
    -p /var/run/docker-desa.pid \
    --iptables=false \
    --ip-masq=false \
    --bridge=none \
    --data-root=/var/lib/docker-desa \
    --exec-root=/var/run/docker-desa
```
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/f235a787-2140-4830-add8-067332085948)

## Ejecutamos el ejecutable.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/6369898a-ffbd-41b4-867e-291b82ab00ec)

## Verificar que este corriendo el nuevo demonio.
![image](https://github.com/julianzanetti/Docker-Udemy/assets/134458575/d3c6f1ea-c723-4061-9408-d3686fc77e11)
