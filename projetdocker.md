# Projet Docker et WSL

Description

J'ai choisi de regrouper tout mon projet sur une seule page GitHub pour que ce soit plus simple à lire et à comprendre. Cela permet à tout le monde de suivre facilement,
surtout qu'il n'y a pas de suite prévue pour ce projet.

#### JOB 01 Mise en place

Ouvrir un terminal administrateur et exécuter :
 
```
 dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
 dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```


Installer Ubuntu

```
wsl --install -d Ubuntu
sudo apt update && sudo apt upgrade
```
Installer Docker 
```
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```
```
sudo apt update
sudo apt install docker-ce -y
docker --version
```

#### JOB 02 Tester docker 
```
sudo service docker start
docker run hello-world
```
#### JOB 03 Création du conteneur "helloworld" depuis une image
```
FROM hello-world
docker build -t my-hello-world .
docker run my-hello-world
```
#### JOB 04 Utilisation de Dockerfile pour créer une image
```
docker pull debian:bullseye
```
Créer un répertoire et un fichier Dockerfile
```
mkdirdocker-ssh
cd docker-ssh
nano Dockerfile 
```
 Dans le Dockerfile
```
FROM debian:bullseye
RUN apt-get update && apt-get install -y openssh-server sudo nano
RUN mkdir /var/run/sshd
RUN echo 'root:root123' | chpasswd
RUN sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config
EXPOSE 2222
CMD ["/usr/sbin/sshd", "-D"]
```
Construire et tester
```
docker build -t mon-image-ssh .
docker run -d -p 2222:22 mon-image-ssh
ssh root@localhost -p 2222
```

#### JOB 05 
```
nano ~/.bashrc
```
```
alias dps='docker ps'  # Afficher les containers en cours d'exécution
alias dpsa='docker ps -a'  # Afficher tous les containers (y compris ceux qui sont arrêtés)
alias drm='docker rm'  # Supprimer un container (ajoutez -f pour forcer la suppression)
alias dimgs='docker images'  # Afficher toutes les images Docker
alias dimgrm='docker rmi'  # Supprimer une image Docker
```
#### JOB 06 Gérer les volumes Docker

Créer un volume :
```
docker volume create xvolume

# Monter le volume dans un conteneur :
docker run -d --name container1 -v xvolume:/data my_image

# Partager le volume entre conteneurs :
docker run -d --name container2 -v xvolume:/data my_image
```










