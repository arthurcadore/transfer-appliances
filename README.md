# Appliances for Transfer Application Protocols 

### This repository is dedicated to simple transfer procotol appliances like FTP, SFTP, SCP and TFTP. Each repository branch has one different protocol appliance. 

Prerequisites
Before you begin, ensure you have the following packages installed on your system:

- Git version 2.34.1
- Docker version 24.0.6, build ed223bc
- Docker Compose version v2.21.0

---
### Getting Started:

First, copy the line below and paste on your prompt to clone the repository:

```
git clone https://github.com/arthurcadore/transfer-servers
```
If you don't have installed the package Git yet, do it before try to clone the respository!

Navigate to the project directory:

```
cd ./transfer-servers
```

If you don't have Docker (and Docker-compose) installed on your system yet, it can be installed by run the following commands (Script for Ubuntu 22.04): 

```
./docker/installDocker.sh
```

**If you had to install docker, please remember to reboot you machine to grant user privileges for docker application.** 

In sequence, configure the user/password variables for the application container access, you can do this by edditing the `docker/Dockerfile` file: 

```
# Add user "capacita" with password "capacitapass"
RUN adduser -D capacita
RUN echo "capacita:capacitapass" | chpasswd

```
In sequence, change the volume mapping point to the home directory of the user named, for example, for the user `capacita`, the volume mapping configuration in `docker-compose.yaml` is: 

```
    volumes:
      - "ssh-keys:/root/.ssh"
      - "./share/:/home/capacita/"

volumes:
  ssh-keys:
```

The volume `ssh-keys` hosts the SSH-keys for the sshD application, remove the docker volume mapping if you want to use the variable of your machine.  

### Start Application's Container: 
Run the command below to start docker-compose file: 

```
docker compose up & 
```

The "&" character creates a process id for the command inputed in, with means that the container will not stop when you close the terminal. 

---

### Access Application:

Once the container is up and running, you can access the application at the ssh://127.0.0.1:2222, as defined (default) in the `docker-compose.yml` file.

--- 
### Stop Container: 
To stop the running container, use the following command:

```
docker-compose down
```

This command stops and removes the containers, networks, defined in the docker-compose.yml file.

--- 



