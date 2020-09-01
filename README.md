# HoksiDockerr (UNDER CONSTRUCTION)
 Pack de utiles para Docker

Las instrucciones de instalación para cada uno de los sistemas compatibles las podéis encontrar aquí:
https://docs.docker.com/engine/install/

Pero en los siguientes apartados os pondré los pasos simplificándolo lo máximo posible:

## Instrucciones para Windows 10 con WSL

1. Actualizar Windows 10 v2004 o superior
2. Instalar WSL 2 usando powershell como admin: 
   ``dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart``
3. Descargar e instalar Docker Container de https://hub.docker.com/editions/community/docker-ce-desktop-windows/
4. Seguir indicaciones de Linux a partir del punto 3. Recomiendo usar la ruta /mnt/c/Users/username/ para guardar los archivos de configuración en vuestra C: o unidad y carpeta deseada.

## Instrucciones para Ubuntu
1. Instalar repositorio Docker usando el Terminal:
   ```
   $ sudo apt-get update

   $ sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
   ```

2. Añadir clave oficial GPG de Docker:
   ```
   $ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
   ```

3. Configurar repositorio "stable":
   ```
   $ sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
   ```

3. Instalar Docker-engine:
   ```
   $ sudo apt-get update
   $ sudo apt-get install docker-ce docker-ce-cli containerd.io
   ```  
5. Instalar Docker Compose:
   ```$ sudo apt install docker-compose```

6. Verificar la correcta instalación con ``$ sudo docker run hello-world``


También podéis usar otros métodos de instalación:
https://docs.docker.com/engine/install/ubuntu/#installation-methods
Para otras distribuciones es muy parecido.

## Instrucciones para Raspberry Pi
1. 


## Instalar HoksiDockerr

1. Ir al directorio donde queréis instalar HoksiDockerr (ejemplo: /home/user)
2. Clonar este git: 
   ``$ git clone https://github.com/hoksilato2/HoksiDockerr``
3. Editar archivo con variables ".env":
   ``$ nano ./HoksiDockerr/Composers/x64-x86/.env``
4. Cambiar los datos de VPN, IP de tu red, carpeta de configuración de las APPS y carpetas donde están tus videotecas en las siguientes variables:

   ```
   ROOT=/home/user/HoksiDockerr
   OPENVPN_PROVIDER=   
   OPENVPN_USERNAME=   
   OPENVPN_PASSWORD=   
   OPENVPN_CONFIG=  
   LOCAL_NETWORK=192.168.0.0/24   
   MOVIES=/media/Pelis   
   TVSHOWS=/media/Series
   ```
   
5. Guardar con ctrl+X + y + enter
6. Ubícate en la carpeta donde está el archivo docker-compose.yml:
   ``$ cd ./HoksiDockerr/Composers/x64-x86/``
7. Instalar compose:
   ``$ docker-compose up -d``
   
Si no habéis hecho coincidir la ruta de ROOT (punto 5) con la carpeta del HoksiDockerr podéis copiar la carpeta config para ahorraros mucha configuración de las APPS:
 
8. Parar todos los containers de docker:
   ``$ docker stop $(docker ps -a -q)``
9. Copiar carpeta de configuración:
   ``$ cp ./HoksiDockerr/config /home/user/HoksiDockerr/config``





