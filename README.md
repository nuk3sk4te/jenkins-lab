# Es necesario montar un volumen persistente para no perder las configs.

docker volume create jenkins-data

Construir la imagen a partir del Dockerfile

docker build -t jenkins-custom -f Dockerfile .

RUN Jenkins:

docker run -v jenkins-data:/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock -v /usr/local/bin/docker:/usr/local/bin/docker -d --name jenkins-cicd -p 8080:8080 -p 50000:50000 jenkins-custom

# Para permitir desplegar sobre el daemon docker del sistema anfitrion, montamos el binario y el daemon de docker. Es una mala práctica solo utilizar para fines educativos.

# Existen ejemplos de pipelines en los proyectos:

MyFavoriteImages-Fronted
MyFavoriteImages-Backend

Tambien podrás encontrar varios ejemplos de Dockerfile y un docker-compose sencillo

Se han instalado plugins recomemdados de Jenkins.

Plan Ejecución de Roadmap 

Masterclass
Talleres
Proyectos
píldoras
