# Cloud-computing
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
1. Create a VM that will host the ELK stack and the web app


2. Secure the VM (using SSH)


3. Set up ELK stack (using Docker) and secure it using TLS protocol

At first you need do set up Docker 🐳

Then you need to set up ELK using docker


Firstly you clone elk using the following command

`$ git clone https://github.com/deviantony/docker-elk `


Then you up the docker compose

`$ sudo docker compose up -d`

> ! If there is an ERROR message try this

`$ dkpg`


4. Create the web app and interconnect it with the REST API of ELK
5. Import data through Log shippers (beat systems) or dummy data from ELK
6. Make queries and observe the results both in Kibana and in the app's UI
