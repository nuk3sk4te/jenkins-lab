# Jenkins Laboratory, (only for Educational Purposes)

Preparación del entorno, iniciar Docker en nuestro equipo.

IMPORTANTE Para Sistemas Windows !! Entrar en linea de comandos 

Desde inicio de Windows, Buscar cmdds y ejecutarlo

Si no tenemos disponible sistema ubuntu instalarlo.

```bash
wsl.exe -l
```
Si solo nos aparece docker-desktop instalar Ubuntu

![image](https://github.com/user-attachments/assets/eed3e651-8333-425d-832e-e1fdf97cba40)

```bash
wsl.exe --install Ubuntu-24.04
```
Si ubuntu no es el sistema prederteminado de WSL, lo cambiaremos con:

```bash
wsl.exe --set-default Ubuntu-24.04
```

Clonar repositorio jenkins-lab a nuestra máquina local. (Podeis utilizar visual studio si os facilita la vida)

```bash
git clone https://github.com/P1-FemCoders-VLC/jenkins-lab.git
```
![image](https://github.com/user-attachments/assets/dbc328ca-4f76-4464-a4a5-7ad47a3c9a1d)

Nos movemos dentro del directorio de trabajo.

```bash
cd jenkins-lab
```

Es necesario montar un volumen persistente para no perder las configs.

```bash
docker volume create jenkins-data
```
Construir la imagen a partir del Dockerfile

```bash
docker build --no-cache -t jenkins-custom -f Dockerfile .
```

Ejecutar el contenedor Jenkins
```bash
docker run -v jenkins-data:/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock -v /usr/local/bin/docker:/usr/local/bin/docker -it --rm --name jenkins-cicd -p 8080:8080 -p 50000:50000 jenkins-custom
```
Para permitir desplegar sobre el daemon docker del sistema anfitrion, montamos el binario y el daemon de docker. 


Acceder vía web al contenedor que acabamos de levantar
http://localhost:8080

![image](https://github.com/user-attachments/assets/cc724bcc-3a43-40d3-b2d7-22f0510c2b8a)

Easy way:
```bash
docker logs jenkins-cicd 
```
Copiar la contraseña generada durante la instalacion y copiarla en la casilla de Administrator password para continuar

Instalar plugins recomendados de Jenkins.
![image](https://github.com/user-attachments/assets/d4b61aae-8c59-4a0d-b6d9-82eab3986f70)

Cambiar la contraseña de administrador y guardarla en el gestor de contraseñas, si no lo hacemos podemos perder acceso a Jenkins
![image](https://github.com/user-attachments/assets/128dbe3c-9c77-4684-96de-188495c3b5b2)


## WARNING !!! Exponer el daemon de docker dentro del contenedor es una mala práctica de seguridad solo utilizar para fines educativos.
