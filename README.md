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
4. Create the web app and interconnect it with the REST API of ELK
5. Import data through Log shippers (beat systems) or dummy data from ELK
6. Make queries and observe the results both in Kibana and in the app's UI
