![image](https://user-images.githubusercontent.com/29571875/129880960-f09a860b-bd90-4d98-9216-761dd5fd640e.png)

- Microservices can be implemented in any languages.
- When the MCs are in different language then deployment become tedious.

**How can we have one way of deploying Go, Java, Python, JavaScript ets. Microservices ?**

- Container comes into picture at this situation to rescue.
![image](https://user-images.githubusercontent.com/29571875/129881625-4d36d8a6-faa7-4ac5-9c7f-d67c99977c16.png)

How to run the MCs after Installing the docker. ?
- Check for version if already installed.

![image](https://user-images.githubusercontent.com/29571875/129883615-b644bd3e-3505-46fc-bc4e-8209d09698e7.png)

- This is location for repositary of your image in docker. But for Enterprise application, there would be separate REPO with private access to download
  image container.
  
  ![image](https://user-images.githubusercontent.com/29571875/129886327-b676c169-6f67-45f8-bd9e-c4066eb666af.png)


![image](https://user-images.githubusercontent.com/29571875/129885123-51429828-42bb-4b5f-bb8e-6338e50a2d3b.png)


To run the application to docker installed VM. Docker run the container on internal docker network and take the default port. So to run on VM where Docker is installed
Below step is to expose the VM particular port to run on that.

![image](https://user-images.githubusercontent.com/29571875/129885537-75515522-edea-45cb-8007-8af687400994.png)

Command to run the containerized application on particular VM port:


![image](https://user-images.githubusercontent.com/29571875/129885998-b9625859-0e69-49ef-afdc-18858f2a90e8.png)

![image](https://user-images.githubusercontent.com/29571875/129886820-407de19b-d9b6-4b1b-a686-43e2412f45fc.png)

We can run multiple container from same image but in different port.

- docker images -> To list all the image in the docker repositary
- docker container ls -> To list all the container image running and stopped both.
- docker logs <docker-image-id>
- docker container stop <container_id> -> Container_id from command docker container ls


# Docker Architecture
  
  - command run the docker client
  - Run command are then sent to Docker Engine
  - Installing DOCKER in local have both Docker CLient and Docker Daemon
  - Docker Engine is responsible for managing the Container, Load Images and pull the docker image from repositary and 
    pushing the locally created images to repositary
  - 

![image](https://user-images.githubusercontent.com/29571875/129888607-b6864029-87e6-4ef5-af98-ecd9150167a5.png)

  
  First it check in the local if not found then download from repositary and run it as container.
  
![image](https://user-images.githubusercontent.com/29571875/129889335-5697d1e3-22c5-4eba-b276-42f560f9bfd1.png)

