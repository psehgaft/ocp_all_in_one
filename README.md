# ocp_all_in_one

## Crear el Certificado Raíz (se hace una vez)
Crear el certificado raíz es fácil y se hace rápidamente. Con estos sencillos pasos se obtiene un certificado SSL raíz que se instalará en todos los escritorios, y una clave privada que se utilizará para firmar los certificados que se instalan en varios dispositivos.

## Crear la clave raíz
El primer paso es crear la clave raíz privada que sólo requiere un paso. En el ejemplo de abajo, estoy creando una clave de 2048 bits:

´´´ openssl
openssl genrsa -out rootCA.key 2048
´´´
