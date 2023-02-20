#### Create resource group
```
az group create \
--name mySQL-rg \
--location northeurope
```

#### Create DB
```
az mysql flexible-server create \
--location northeurope \
--resource-group mySQL-rg \
--name bbcuek210bmindy \
--admin-user username \
--admin-password password
```

#### Connect to DB (optional)
```
az mysql flexible-server connect \
--name bbcuek210bmindy \
--admin-user username \
--admin-password password \
--interactive
```


#### Delete (optional)
```
az mysql flexible-server delete \
--resource-group mySQL-rg \
--name bbcuek210bmindy
```
    