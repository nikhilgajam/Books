# Docker

**1. Introduction**

The evolution of computing technology has significantly transformed the way we develop, deploy, and manage applications. One notable transition is the shift from traditional virtualization to containerization, with Docker leading the way. In this document, we will explore how Docker evolved from the basics of virtualization.

**2. Virtualization Basics**

Virtualization is the practice of creating multiple virtual instances, or Virtual Machines (VMs), on a single physical server. Each VM runs its own operating system (OS) and applications, isolated from the others. Key elements of virtualization include:

- **Hypervisor**: A software or hardware layer that manages and allocates physical server resources to VMs.

- **Guest OS**: Each VM has its own complete OS stack, including kernel, libraries, and applications.

- **Resource Overhead**: VMs consume significant resources due to running complete OS instances, resulting in slower startup times and higher resource consumption.

**3. Docker: The Containerization Revolution**

Docker is a containerization platform that introduced a revolutionary approach to application deployment. Containers are lightweight, portable, and isolated environments that package applications and their dependencies. Key aspects of Docker include:

- **Containerization**: Docker containers package an application and its dependencies into a single, self-sufficient unit.

- **Docker Engine**: The core component that allows container creation, management, and execution.

- **Shared Kernel**: Containers share the host OS kernel, reducing resource overhead and enabling faster startup times.

- **Docker Hub**: A repository for sharing and distributing Docker images.


**4. Key Differences Between Virtualization and Docker**

Let's examine the fundamental differences between traditional virtualization and Docker containerization:

- **Resource Efficiency**: Virtualization consumes more resources because each VM runs a complete OS, while containers share the host OS, reducing overhead significantly.

- **Isolation**: VMs offer stronger isolation since they run separate OS instances. Containers share the OS kernel, providing efficient isolation but not as strong as VMs.

- **Startup Time**: Containers start almost instantly, whereas VMs may take minutes to boot.

- **Portability**: Docker containers are highly portable, allowing applications to run consistently across various environments.

- **Footprint**: Containers have a smaller footprint due to shared resources, making them ideal for microservices architecture.


**5. Advantages of Docker Over Traditional Virtualization**

The adoption of Docker and containerization has gained momentum due to several advantages:

- **Resource Efficiency**: Docker containers are lightweight and efficient, allowing for more efficient use of hardware resources.

- **Portability**: Containers are highly portable and can run consistently across different environments, from development to production.

- **Rapid Deployment**: Containers start quickly, enabling faster application deployment and scaling.

- **Version Control**: Docker images can be version-controlled, facilitating reproducible deployments.

- **Orchestration**: Tools like Kubernetes can be used to manage and orchestrate containerized applications at scale.

**6. Use Cases and Practical Applications**

Docker has found extensive use in various industries and application scenarios:

- **Microservices Architecture**: Containerization is ideal for breaking down monolithic applications into smaller, manageable microservices.

- **Continuous Integration/Continuous Deployment (CI/CD)**: Docker simplifies the packaging and deployment of applications in CI/CD pipelines.

- **DevOps Practices**: Docker and containerization align well with DevOps principles, enabling rapid and automated deployments.

- **Cloud-Native Applications**: Docker is a foundational technology for cloud-native applications that need to scale dynamically.

**7. Conclusion**

In summary, Docker has evolved from the traditional virtualization model by introducing containerization, which offers improved resource efficiency, portability, and faster deployment times. This transformation has revolutionized how applications are developed, deployed, and managed in modern computing environments. As the adoption of containers continues to grow, Docker remains at the forefront of this transformative shift in the IT landscape.

https://docs.docker.com/engine/install/rhel/

In the context of Docker and containerization, "images," "containers," "registries," and "Dockerfiles" are fundamental concepts:

1. **Docker Image:**
  - A Docker image is a lightweight, standalone, and executable package that contains all the necessary code, libraries, and dependencies to run a software application.
  - Images are read-only and provide a consistent environment for running applications, regardless of the host system.
  - Images are used as templates to create containers. You can think of them as snapshots of a filesystem with an application and its dependencies.
2. **Docker Container:**
  - A Docker container is a running instance of a Docker image. It encapsulates the application and its environment in an isolated process.
  - Containers are lightweight, portable, and can be easily started, stopped, and moved between different environments without affecting the host system.
  - Containers provide process isolation and resource constraints, allowing multiple containers to run on the same host without conflicts.
3. **Docker Registry:**
  - A Docker registry is a central repository for storing and sharing Docker images. It serves as a distribution point for Docker images, allowing users to upload and download images.
  - Docker Hub is a popular public registry where you can find a wide range of pre-built Docker images. You can also set up private registries for your organization's use.
  - When you run `docker pull` or `docker run`, Docker retrieves images from a registry (by default, Docker Hub) unless specified otherwise.
4. **Dockerfile:**
  - A Dockerfile is a plain-text configuration file that defines the instructions and steps needed to build a Docker image.
  - Dockerfiles contain commands to copy files into the image, set environment variables, install packages, and configure the image's behavior.
  - By using Dockerfiles, you can create custom Docker images tailored to your application's requirements. Building an image from a Dockerfile ensures reproducibility and consistency.
Here's how these concepts work together:
- A Dockerfile is used to define how an image should be constructed. It includes all the instructions needed to prepare the environment for your application.
- You build a Docker image using the Dockerfile and the `docker build` command.
- Once you have a Docker image, you can store it in a Docker registry (public or private) for others to use or for deployment to different environments.
- To run an application, you create a Docker container from an image using the `docker run` command. Containers are instances of images and are isolated from each other and the host system.
- Containers can be started, stopped, and deleted independently, making them a flexible and scalable way to deploy and manage applications.
Overall, Docker simplifies application deployment by packaging everything needed to run an application into a single, portable unit (the image) and then creating isolated instances (containers) that can be managed and scaled efficiently. Images, containers, registries, and Dockerfiles are core components of this containerization technology.

# Docker Commands:

## Example Dockerfile

- Filename: Dockerfile
- Dockerfile is used to configure docker container
```
FROM python

WORKDIR /app

COPY ./server.py .
# COPY ./dist /app  # Or ./dist .

RUN pip install requests  # Downloading external modules

CMD ["python", "server.py"]
# CMD ["npx", "serve", "-s", "dist"]   # Actual Command: npx serve -s dist
```

## Build
- ```docker build .``` (builds everything in the pwd)
- ```docker build -t app:01``` (tagging name:version)

## Run
- ```docker run -d --hostname my-rabbit --name some-rabbit -p 5672:5672 -p 15672:15672 rabbitmq:3-management```
- ```docker run --name redis -p 6379:6379 -d redis``` (detached mode)
- ```docker run -d --rm app``` (runs in detached mode and deletes when program in the docker stops)
- ```docker run -d --rm --name "some_name" -p machine_port:docker_port app imageid``` (adding name)
- ```docker run -d --rm --name "some_name" -p machine_port:docker_port app imagename:version``` (run with image name and version)
- ```docker run -it ubuntu``` (interactive mode)

## Logs
- ```docker logs podname```

## Volume
- ```docker run -it --rm -v volumename:/imagename``` (Volume and data in that will persist even after the container is deleted)
- ```docker volume ls``` (List all volumes)

## Mount Bind
- ```docker run -v /User/nikhil/project/services.txt:/app/services.txt --rm imageidOrname``` (Binding local path to volume)

## List
- ```docker images``` (all images)
- ```docker ps -a``` (all containers)
- ```docker ps``` (running containers)

## Stop
- ```docker stop containerid```
- ```docker stop containername```

## Remove
- ```docker rm container_name``` (containerId)
- ```docker rmi image_name```	(imageId)

## Container info
- ```docker inspect containername```

## Dockerhub pulling
- ```docker pull image_name```
- ```docker run image_name```

Ex:
```
docker pull mysql
docker run -d --env MYSQL_ROOT_PASSWORD="root" --env MYSQL_DATABASE="TableName" --name mysqldb mysql  (Providing the environment variables)
docker logs mysqldb
```

## Docker and DBMS
- Use ```host="host.docker.internal"``` for any DB connection instead of ```host="localhost"```
- When trying to connect two pods one with program to connect DBMS and another with MySQL DBMS then use ```docker inspect podname``` and in NETWORK section use the IPAddress as host in the program.

## Network
- ```docker network create my-net```
- ```docker network create -d bridge my-network``` (network in detach mode)
- ```docker network ls``` (List all networks)
- ```docker run -d --env MYSQL_ROOT_PASSWORD="root" --env MYSQL_DATABASE="TableName" --name mysqldb --network my-net mysql```
We can use ```mysqldb``` as the host in the program to connect to DB
docker network rm my-net

```
docker run --name some-mongo --network my-network -d mongo (server)
docker run -it --network my-network --rm mongo mongosh --host some-mongo test (client)

docker run --name some-postgres -e POSTGRES_PASSWORD=mysecretpassword -d postgres
docker exec -it some-postgres bash (iteractive bash mode)
	/# psql -h localhost -U postgres

docker run --name some-nginx -v D:/demo:/usr/share/nginx/html -p 8888:80 -d nginx (volume mounting & port mapping/binding)
docker exec -it some-nginx bash
docker stop some-nginx
docker rm some-nginx
```

## Example docker compose file
- filename: docker-compose.yml
```
services:
  mysqldb:
    image: 'mysql:latest'
    environment:
      - MYSQL_ROOT_PASSWORD=root
      - MYSQL_DATABASE=Users
    container_name: 'mysqldb'
    healthcheck:
      test: ['CMD', 'mysqladmin', 'ping', '-h', 'localhost']
      timeout: 20s
      retries: 10
  
  app:
    build: ./ # Dockerfile path and uses host='mysqldb' compose creates network automatically
    ports:
      - 8080:3000
    container_name: 'mypyapp'
    networks:
      - appnet
    volumes:
      - ./server.txt # Mount binding the file
    depends_on:
      mysqldb:
        condition: service_healthy # When we run the services concurrently then mysqldb is run first waits until and app uses that
    stdin_open: true
    tty: true

  networks:
    appnet:

# Refer for more info: https://docs.docker.com/reference/compose-file/services/
```

## Run all images using one docker file
- ```docker-compose up -d```
- ```docker-compose down```

- ```docker-compose run -d mysqldb``` (Run services from the docker-compose.yml file)
- ```docker-compose run app``` (This uses interactive mode so takes input from the user and as app depends on mysqldb if we run app both services will be up)

- ```docker-compose down -v```  (To delete volumes and networks)

## Kubernetes Commands:
- **List Services:** ```k get po```
- **Filter Services:** ```kubectl get pods | grep pattern```
- **Execute Commands In POD:** ```k exec -it name -- node -v```
- **Image Info:** ```k describe pod name | grep -i IMAGE```
- **POD Logs:** ```k logs podname –tail=10```
- **Restart Cluster:** ```kubectl rollout restart deployment/name```
- **Delete POD:** ```kubectl get pods -o name | grep fit | xargs kubectl delete```
- **Delete And Restart:** ```kubectl delete podname```
- **Scaling Down:** ```k scale --replicas=0 deployment/name```
- **Scaling Up:** ```k scale --replicas=count deployment/name```
- **Checking Files:** ```k exec -it podname -- cat something/filename.ext```
- **Checking Node ENV Variables:**  ```kubectl exec -it podname -- /bin/sh -c 'node -e "console.log(process.env)"'```
