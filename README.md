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

Se pedirá que se introduzca una contraseña, y desde entonces se retará a introducir la contraseña cada vez que se use la clave. Claro, si olvidads la clave tendrás que hacer todo esto de nuevo.

El siguiente paso es autofirmar este certificado

``` openssl
openssl req -x509 -new -nodes -key rootCA.key -days 1024 -out rootCA.pem
```

Lo que comenzará un script interactivo que preguntará información. Como se muestra acontinuacion:

``` openssl
tzulkin@Franciscos-MBP .ssh % openssl req -x509 -new -nodes -key rootCA.key -days 1024 -out rootCA.pem
Enter pass phrase for rootCA.key:
You are about to be asked to enter information that will be incorporated
into your certificate request.
What you are about to enter is what is called a Distinguished Name or a DN.
There are quite a few fields but you can leave some blank
For some fields there will be a default value,
If you enter '.', the field will be left blank.
-----
Country Name (2 letter code) []:MX
State or Province Name (full name) []:CDMX
Locality Name (eg, city) []:CDMX
Organization Name (eg, company) []:Delibanez
Organizational Unit Name (eg, section) []:it
Common Name (eg, fully qualified host name) []:delibanezit.com
Email Address []:jazmin@delibanezit.com
tzulkin@Franciscos-MBP .ssh % ls -lrs                                                                 
total 176
 8 -rw-r--r
```


