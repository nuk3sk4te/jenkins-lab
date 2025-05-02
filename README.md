# Jenkins Laboratory, (only for Educational Purposes)

Preparación del entorno, iniciar Docker en nuestro equipo.

IMPORTANTE Para Sistemas Windows !! Entrar a WSL 

![image](https://github.com/user-attachments/assets/b16ca45d-0395-42f8-890d-5bd23e761090)

Clonar repositorio jenkins-lab a nuestra máquina local.

```bash
git clone https://github.com/nuk3sk4te/jenkins-lab.git
```
![image](https://github.com/user-attachments/assets/e6d5d88c-2b35-4473-bde3-b4f8013ed752)



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
docker build -t jenkins-custom -f Dockerfile .
```

Ejecutar el contenedor Jenkins
```bash
docker run -v jenkins-data:/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock -v /usr/local/bin/docker:/usr/local/bin/docker -d --name jenkins-cicd -p 8080:8080 -p 50000:50000 jenkins-custom
```
Para permitir desplegar sobre el daemon docker del sistema anfitrion, montamos el binario y el daemon de docker. 


Acceder vía web al contenedor que acabamos de levantar
http://localhost:8080

Instalar plugins recomemdados de Jenkins.




## WARNING !!! Exponer el daemon de docker dentro del contenedor es una mala práctica de seguridad solo utilizar para fines educativos.
