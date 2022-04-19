# Ejemplo de uso de caché en NGINX

Este ejemplo resuelve el reto de tener varias cachés en NGINX, incluyendo una caché global y una caché por usuario.

## Guía rápida de uso

Las tres peticiones que podemos lanzar son:

```sh
curl -v -H "Authorization: Bearer 12345" -X GET http://localhost:8080/global/ # cache global

curl -v -H "Authorization: Bearer 12345" -X GET http://localhost:8080/user/ # cache de usuario
curl -v -H "Authorization: Bearer 54321" -X GET http://localhost:8080/user/ # cache de usuario, cambiando bearer

curl -v -H "Authorization: Bearer 12345" -X GET http://localhost:8080/none/ # sin cache
```

A medida que se hagan distintas peticiones, observar el comportamiento de los directorios `./cache/global` y `./cache/user`.

## Limpiar cachés para repetir el experimento

Para borrar el directorio `./cache`:

```sh
find ./cache/ -not -name '.gitkeep' -delete
```