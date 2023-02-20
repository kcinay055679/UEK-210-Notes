## Create spring app
#### Create resource group
```
az group create \
--name springApplication-rg \
--location northeurope
```

#### Create spring service
```
az spring create \
--resource-group springApplication-rg \ 
--name bmindy-application-service
```

#### Create spring app
```
az spring app create \
--resource-group springApplication-rg \
--service bmindy-application-service \
--name bmindy-application \
--runtime-version Java_17 \
--assign-endpoint true
```

#### Create db
```
az mysql flexible-server create \
--location northeurope \
--resource-group springApplication-rg \
--name bmindy-spring-db \
--admin-user username \
--admin-password password \
--database-name spring
```

#### Connect to db
```
az mysql flexible-server connect \
--name bmindy-spring-db \
--admin-user username \
--admin-password password  \
--interactive
```

#### Disable TLS enforcement
```
az mysql flexible-server \
parameter set  \
--resource-group springApplication-rg  \
--server-name bmindy-spring-db  \
--name require_secure_transport  \
--value OFF 
```

#### Create connection between spring application and DB
```
az spring connection create mysql-flexible \
-g springApplication-rg \
--tg springApplication-rg \
--connection bmindystudleconnection \
--service bmindy-application-service \
--app bmindy-application \
--server bmindy-spring-db \
--database spring \
--client-type springBoot \
--secret name=username secret=password
```

#### Deploy jar file
```
az spring app deploy \
--resource-group springApplication-rg \
--service bmindy-application-service \
--name bmindy-application \
--artifact-path studle-app.jar
```

#### Get URL
```
az spring app list \
-g springApplication-rg \
-s bmindy-application-service
```