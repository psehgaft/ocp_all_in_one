# ocp_all_in_one

## Crear el Certificado Raíz (se hace una vez)
Crear el certificado raíz es fácil y se hace rápidamente. Con estos sencillos pasos se obtiene un certificado SSL raíz que se instalará en todos los escritorios, y una clave privada que se utilizará para firmar los certificados que se instalan en varios dispositivos.

## Crear la clave raíz
El primer paso es crear la clave raíz privada que sólo requiere un paso. En el ejemplo de abajo, estoy creando una clave de 2048 bits:

``` openssl
openssl genrsa -out rootCA.key 2048
```

Los tamaños de clave estándar actuales son 1024, 2048 y, aunque mucho menos extendido, 4096. Elegiremos para este ejemplo [2048], que es el más utilizado hoy en día. 4096 en el futuro seria una mejor opcion.

Nota importante: Mantener esta clave privada muy privada. Ésta es la base de toda confianza para tus certificados, y si alguien obtiene una copia, podría generar certificados que acepte el navegador. También se puede crear una clave que esté protegida mediante una contraseña añadiendo -des3:

``` openssl
openssl genrsa -out rootCA.key 2048 -des3
```
