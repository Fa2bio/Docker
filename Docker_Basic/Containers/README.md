<h1>Docker-Containers</h1>

### Show Containers In Use
```xml
docker ps
```

### Show Containers Created
```xml
docker ps -a
```

### Stop Containers
```xml
docker kill $(docker ps -q)
```

### Stop A Container
```xml
docker stop myContainer
```

### Start A Container
```xml
docker start myContainer
```

### Displays All Logs From a Container
```xml
docker container logs myContainer
```

### Displays In Json Format All Container Information
```xml
docker container inspect myContainer
```

### Delete A Container
```xml
docker rm containerId
```

### Delete All Containers
```xml
docker rm -f $(docker ps -a -q)
```