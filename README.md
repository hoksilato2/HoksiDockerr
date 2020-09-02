# HoksiDockerr (UNDER CONSTRUCTION)
 Pack de utiles para Docker

Las instrucciones de instalación para cada uno de los sistemas compatibles las podéis encontrar aquí:
https://docs.docker.com/engine/install/

Pero en los siguientes apartados os pondré los pasos simplificándolo lo máximo posible:

## Instalar Docker

### Windows 10 con WSL

1. Actualizar Windows 10 v2004 o superior
2. Instalar WSL 2 usando powershell como admin: 
   ```
   dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
   ```
3. Descargar e instalar Docker Container de https://hub.docker.com/editions/community/docker-ce-desktop-windows/
4. Seguir indicaciones de Linux a partir del punto 3. Recomiendo usar la ruta /mnt/c/Users/username/ para guardar los archivos de configuración en vuestra C: o unidad y carpeta deseada.

### Ubuntu
0. Puedes encontrar Docker en el repositorio Canonical. Pero si prefieres usar el repositorio Docker sigue hasta el punto 5.
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
   ```
   $ sudo apt install docker-compose
   ```

6. Verificar la correcta instalación con ``$ sudo docker run hello-world``


También podéis usar otros métodos de instalación:
https://docs.docker.com/engine/install/ubuntu/#installation-methods
Para otras distribuciones es muy parecido.

### Raspberry Pi
1. 


### Instalar HoksiDockerr

1. Ir al directorio donde queréis instalar HoksiDockerr (ejemplo: /home/user)
2. Clonar este git: 
   ```
   $ git clone https://github.com/hoksilato2/HoksiDockerr
   ```
3. Editar archivo con variables ".env":

  en Windows / Ubuntu:
   ```
   $ nano ./HoksiDockerr/Composers/x64-x86/.env
   ```
 en Raspi:
   ```
   $ nano ./HoksiDockerr/Composers/raspi-arm/.env
   ```  
   
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

   En Win/Ubuntu:
   ```
   $ cd ./HoksiDockerr/Composers/x64-x86/
   ```
   En Raspi:
   ```
   $ cd ./HoksiDockerr/Composers/raspi-arm/
   ```   
   
7. Instalar compose:
   ```
   $ sudo docker-compose up -d
   ```
   
8. Reiniciar todos los contenedores:
   ```
   sudo docker restart $(sudo docker ps -a -q)
   
   
Si no habéis hecho coincidir la ruta de ROOT (punto 4) con la carpeta del HoksiDockerr podéis copiar la carpeta config para ahorraros mucha configuración de las APPS:
 
9. Parar todos los containers de docker:
   ```
   $ sudo docker stop $(sudo docker ps -a -q)
   ```
10. Copiar carpeta de configuración:
   ```
   $ cp ./HoksiDockerr/config /home/user/HoksiDockerr/config
   ```


## Configurar Aplicaciones

Para acceder a cada una de las aplicaciones lo podremos hacer mediante las siguientes direcciones:

   **Transmission** (cliente Torrent): http://localhost:9091

   **Jackett** (indexador): http://localhost:9117
    
   **Sonarr** (Buscador de Series): http://localhost:8989
    
   **Radarr** (Buscador de Películas): http://localhost:7878
    
   **Bazarr** (Buscador de subtítulos): http://localhost:6767
    
    
### Sustitución de IPs

Para que las aplicaciones se vean entre ellas, deberás facilitar la dirección IP de tu equipo. Al estar dentro de Docker, no funcionará ni "localhost" ni "127.0.0.1" ya que cada contenedor es como un ordenador distinto con su propia IP. Pero no hace falta configurar cada IP dado que de manera "externa" reconocerá la IP de nuestra red local.

De todas formas, si quieres saber las IPs de cada uno de los contenedores puedes usar este comando:

```
docker ps -q | xargs -n 1 docker inspect --format '{{ .Name }} {{range .NetworkSettings.Networks}} {{.IPAddress}}{{end}}' | sed 's#^/##';
```

**Para saber la IP local de tu equipo:**

en Linux: ``$ if config eth0`` (ej: inet 192.168.0.117)
    
en Windows: ``ipconfig | findstr /i "ipv4"`` (en CMD no en WSL. Si tienes más de una tarjeta de red, la ethernet es la primera)
    

**¿Dónde cambiar las IPs?**

En Sonarr y Radarr: 

*Settings > Indexers >* Entrar en cada uno de ellos y sustituir la IP que hay en el campo URL (La IP de Jackett o la local)

*Settings > Download Client > Transmission > Host* (La IP de Transmission o la local)
                               
En Bazarr: 

*Settings > Sonarr > "Hostname or IP Address"* (La IP de Sonarr o la local)

*Settings > Radarr > "Hostname or IP Address"* (La IP de Radarr o la local)
                      
                      

                      







