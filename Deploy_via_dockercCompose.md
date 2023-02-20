## Publsh application via docker compose
#### Create new resource group
```
az group create \
--name dockerCompose-rg \
--location northeurope
```

#### Create new container registry
```
az acr create \
--resource-group dockerCompose-rg \
--name bmindyuek210 \
--sku Basic
```

#### Login  into the new continaer registry
`az acr login --name bmindyuek210`

#### Get subscription id 
`az group list `

#### Create new service principle
```
az ad sp create-for-rbac \
--scopes /subscriptions/5969103f-760c-44ed-8c9b-145f441fc72d \
--role "Owner"
```

##### Save output for later

#### Login into registry with docker 
`docker login bmindyuek210.azurecr.io`


##### Credentials 
Username: APPID
Password: PASSWORD

#### Use docker to login into azure
`docker login azure`

#### Create new docker context on azure
`docker context create aci portainer`

#### Use the new context
`docker context use portainer`

#### Navigate into folder with docker-compose.yml (optional)
`cd directory`

#### Start docker container 
`docker compose up`