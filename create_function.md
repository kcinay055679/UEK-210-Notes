## Create serverless function
#### Create new project
  ```
  func init serverlessFunctions \
  --javascript
  ```
##### Change into directory
 `cd serverlessFunctions`

#### Create new function
```
func new \
--name httpFunction  \
--template "HTTP trigger" \
--authlevel "anonymous"
```
##### Start function local (optional)
`func start`

#### Login into azure
`az login`

#### Create new resource group
```
az group create \
--name AzureFunctionsQuickstart-rg \
--location northeurope
```

#### Create new storage account
```
az storage account create \
--name bbcuek210bmindystorage \
--location northeurope \
--resource-group AzureFunctionsQuickstart-rg \
--sku Standard_LRS
```

#### Create new function on azure
```
az functionapp create \
--resource-group AzureFunctionsQuickstart-rg \
--consumption-plan-location northeurope \
--runtime node \
--runtime-version 18 \
--functions-version 4 \
--name servelessFunction \
--storage-account bbcuek210bmindystorage
```

#### Start/ Publish function
`func azure functionapp publish servelessFunction`

