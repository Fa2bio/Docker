<h1>Docker-Basic</h1>

### Start Docker Service
```xml
sudo systemctl start docker
```

### Stop Docker Service
```xml
sudo systemctl stop docker
```

### Show Containers In Use
```xml
docker ps
```

### Stop Containers
```xml
docker kill $(docker ps -q)
```

### Stop A Container
```xml
docker stop myContainer
```
