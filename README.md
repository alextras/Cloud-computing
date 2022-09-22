# Cloud-computing ☁️
This is a repository for the semester project in cloud computing

**Aim** of the project is:
- to create a **web app** 
  - which queries from **Elasticsearch**
  - using Java (Maven or Spring Boot)
- to describe the process and the difficulties in building
  - the web app
  - the ELK stack
  - the secure function of ELK stack using the TLS protocol


**Steps** that will be followed:
## 1. Create a VM that will host the ELK stack and the web app
We create the VM using VirtualBox as the hypervisor
For more info on how to download VirtualBox

At first we download an Ubuntu server image which will be the OS that wil be installed in the VM and then we make the specific configurations.

The VM should have the following features:
- OS: Ubuntu server 18.04 LTS
- System memory / RAM: 4 GB (at least)
- CPU: 2 GHz dual core processor
- Hard drive space: 60 GB (at least)
- Network: Bridged


## 2. Secure the VM (using SSH)
In order to secure the VM we set up the SSH server

Steps:

1. We remove existing SSH servers that may have issues

```console
sudo apt-get remove openssh-server
```

2. We install the ssh 
```console
sudo apt-get install openssh-server
```

3. We check the SSH server status to be active
```console
sudo service status ssh
```


Then we secure the SSH by the following steps

1. Change default port

We change the default port #22 to another one


2. Disable root logins 

In sshd_config we set PermitRootLogin to no

3. RSA cryptography



## 3. Set up ELK stack (using Docker) and secure it using TLS protocol

### Docker setup
At first you need to install Docker Engine 🐳

Uninstall old versions
```console
sudo apt-get remove docker docker-engine docker.io containerd runc
```
Set up the repository
1. Update the apt package index and install packages to allow apt to use a repository over HTTPS
```console
sudo apt-get update
sudo apt-get install \
  ca-certificates \
  curl \
  gnupg \
  lsb-release
```

2. Add Docker’s official GPG key:
```console
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

3. Use the following command to set up the repository:
```console
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

Install Docker Engine
1. Update the apt package index, and install the latest version of Docker Engine, containerd, and Docker Compose,
```console
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

2. Verify that Docker Engine is installed correctly by running the hello-world image.
```console
sudo service docker start
sudo docker run hello-world
```

### ELK setup
Then you need to set up ELK using docker

Firstly we clone an existing repository into a new directory using the following command

```console
git clone https://github.com/deviantony/docker-elk
```

the name of the new directory is `docker-elk` and it contains all the docker images needed to setup elk containers

Then we create and start the containers using docker compose 
```console
sudo docker compose up -d
```

- `docker compose`: command is responsible to define and run multi-container applications with Docker
- `docker compose up`: creates and starts containers
- `-d` flag: enables detached mode (runs containers in the background)

> ! If there is an ERROR message about .env files try removing docker-credential-helpers with the following command:
> ```console
> dpkg -r --force-depends golang-docker-credential-helpers
> ```

### Filebeat installation
Install filebeat as a service

**Step 1. Install filebeat**
```console
curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-8.3.3-amd64.deb
sudo dpkg -i filebeat-8.3.3-amd64.deb
```

**Step 2. Connect to the Elastic Stack**

**Step 3: Collect log data**

**Step 4. Set up assets**
```console
filebeat setup -e
```

**Step 5: Start Filebeat**
```console
sudo service filebeat start
```

**Step 6: View your data in Kibana**
Point your browser to http://localhost:5601, replacing `localhost` with the name of the Kibana host



## 4. Create the web app and interconnect it with the REST API of ELK


## 5. Import data through Log shippers (beat systems) or dummy data from ELK


## 6. Make queries and observe the results both in Kibana and in the app's UI
