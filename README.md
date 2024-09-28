I'm referring [Blog](https://arinco.com.au/blog/azure-mlops-challenge-blog-part-2/) along with [Microsoft challenge](https://microsoftlearning.github.io/mslearn-mlops/documentation/01-aml-job).

To install Az CLI ```brew update && brew install azure-cli```

AZ commands executed:
- Create Resource Group

  ```az group create --name rgMlOps --location australiaeast```

- Create Workspace

  ```az ml workspace create --resource-group rgMlOps --name wsMlOps```

- Create a compute cluster

  ```az ml compute create --name ccMlOps --size Standard_DS3_v2 --type AmlCompute --workspace-name wsMlOps --resource-group rgMlOps```

- Create dataset asset in workspace ```az ml data create --file dataset.yml --workspace-name wsMlOps --resource-group rgMlOps```, with file dataset.yml it will upload CSV data to default datastore.
The default datastore for workspace would be the storage account created along with the workspace.

- Create train job, as defined in job.yml file with CLI command

``` az ml job create --file src/job.yml --workspace-name wsMlOps --resource-group rgMlOps ```