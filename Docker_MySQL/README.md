<h1>MySQL</h1>

### Docker pull
```xml
docker pull mysql:latest
```

### Start A Custom Container
```xml
docker run -p 3307:3306 --name mysql -e MYSQL_ROOT_PASSWORD=password -d mysql:latest
```
