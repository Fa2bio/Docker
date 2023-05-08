<h1>SpringBoot - MySQL</h1>

## Contents

* [Requirements](#requirements)
* [How to create a docker image of the SpringBoot application](#image)
* [Containers](#containers)

## <a name="requirements"></a>Requirements

- A MySQL Docker image
- A Docker image of the SpringBoot application

## <a name="image"></a>How to create a docker image of the SpringBoot application

Now let's externalize the connection settings between the Spring Boot project and the MySQL server defined in application.properties. For this, we'll create environment variables that will be used to customize the connection to the database

### application.properties
```xml
spring.datasource.url=jdbc:mysql://${MYSQL_HOST:localhost}:${MYSQL_PORT:3306}/dbname?createDatabaseIfNotExist=true
spring.datasource.username=${MYSQL_USER:user}
spring.datasource.password=${MYSQL_PASSWORD:password}
```
<br></br>
Once that's done, let's package the SpringBoot application into a .jar executable using the Maven tool. Through an IDE that has Maven built-in - go to Run As -> Maven build

![1673543893216](https://user-images.githubusercontent.com/41877566/236881119-0d6921d0-a210-46e0-93ad-5b10b730652d.png)

<br></br>
Now let's create the Dockerfile that will be responsible for creating our image from our SpringBoot application

### Dockerfile
```xml
FROM openjdk

WORKDIR /app

COPY target/MySpringBootApp-0.0.1-SNAPSHOT.jar /app/springbootproject.jar

ENTRYPOINT ["java", "-jar", "springbootproject.jar"]
```
<br></br>
Now let's build the image, for that we will open a terminal in the root folder and execute the instruction:

### Terminal
```xml
docker build -t springbootproject .
```
<br></br>
## <a name="containers"></a>Containers

- Now that the images are ready, let's move on to the containers. Let's start by starting a container for MySQL.

### Terminal
```xml
docker run -p 3307:3306 --name dbname -e MYSQL_ROOT_PASSWORD=password -d mysql
```
<br></br>
Now let's create a network for the MySQL container to communicate with the future container of our Spring Boot project

### Terminal
```xml
docker network create spring-net
```
<br></br>
Now let's associate our database with the spring-net network

### Terminal
```xml
docker network connect spring-net dbname
```
<br></br>
Now, finally let's create our container for the Spring Boot project

### Terminal
```xml
docker run -p 9090:8080 --name springbootproject --net spring-net -e MYSQL_HOST=dbname -e MYSQL_USER=root -e MYSQL_PASSWORD=password -e MYSQL_PORT=3306 -d springbootproject
```
