<h1>SpringBoot - MySQL</h1>

## Contents

* [Requirements](#requirements)
* [How to create a docker image of the SpringBoot application](#installation)
* [Diagrams](#uml)

## <a name="requirements"></a>Requirements

- A MySQL Docker image
- A Docker image of the SpringBoot application

## <a name="installation"></a>How to create a docker image of the SpringBoot application

- Now let's externalize the connection settings between the Spring Boot project and the MySQL server defined in application.properties. For this, we'll create environment variables that will be used to customize the connection to the database.

### application.properties
```xml
spring.datasource.url=jdbc:mysql://${MYSQL_HOST:localhost}:${MYSQL_PORT:3306}/dbname?createDatabaseIfNotExist=true
spring.datasource.username=${MYSQL_USER:user}
spring.datasource.password=${MYSQL_PASSWORD:password}
```

- Once that's done, let's package the SpringBoot application into a .jar executable using the Maven tool. Through an IDE that has Maven built-in - go to Run As -> Maven build
