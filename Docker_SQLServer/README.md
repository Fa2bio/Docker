<h1>SQLServer</h1>

### Docker pull
```xml
docker pull mcr.microsoft.com/mssql/server:2019-latest
```

### Start Container
```xml
docker run --name sqlserver -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=MsProject@2022" -p 1433:1433 -d mcr.microsoft.com/mssql/server:2019-latest
```
