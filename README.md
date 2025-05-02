# Jenkins Laboratory, (only for Educational Purposes)

Preparación del entorno, iniciar Docker en nuestro equipo.

Clonar repositorio jenkins-lab a nuestra máquina local.

```bash
git clone https://github.com/nuk3sk4te/jenkins-lab.git
```

Nos movemos dentro del directorio de trabajo.

```bash
cd jenkins-data
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
## WARNING !!!  Es una mala práctica solo utilizar para fines educativos.

Acceder vía web al contenedor que acabamos de levantar
http://localhost:8080

Instalar plugins recomemdados de Jenkins.


