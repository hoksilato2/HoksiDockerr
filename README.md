# HoksiDockerr
 Pack de utiles para Docker


## Instrucciones para Windows 10 con WSL

1. Actualizar Windows 10 v2004 o superior
2. Instalar WSL 2
3. Descargar e instalar Docker Container
4. Seguir indicaciones de Linux a partir del punto X.

## Instrucciones para Linux
1. Instalar Docker:

2. Instalar Docker Compose:

3. Clonar este git: 
   git clone https://github.com/hoksilato2/HoksiDockerr
4. Editar archivo con variables ".env":
   nano ./HoksiDockerr/Composers/x64-x86/.env
5. Cambiar datos de VPN, IP de tu red, carpeta de configuración de las APPS y carpetas donde están tus videotecas en las siguientes variables:
   OPENVPN_PROVIDER=
   OPENVPN_USERNAME=
   OPENVPN_PASSWORD=
   OPENVPN_CONFIG=
   LOCAL_NETWORK=192.168.0.0/24
   MOVIES=/media/Pelis
   TVSHOWS=/media/Series
   
6. Guardar con ctrl+X + y + enter
7. Ir a la carpeta donde está el archivo "compose":
   cd ./HoksiDockerr/Composers/x64-x86/
8. Instalar compose:
   docker-compose up -d
9. parar todos los containers de docker:
   docker stop $(docker ps -a -q)
10. Copiar carpeta de configuración (optativo):
   cp ./HoksiDockerr/config /home/user/Docker/config


## Instrucciones para Raspberry Pi
1. Seguir indicaciones hasta punto X

