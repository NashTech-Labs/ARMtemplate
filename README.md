# ARMtemplate

This is Azure Resource Manager (ARM) template file to provision storage in Azure Cloud. Using this, you can provision other resources on Azure as well.

## Steps

### 1. Install Azure Powershell or Azure CLI locally

 Because to deploy a local template, you need to have either Azure PowerShell or the Azure CLI installed locally.

 reference:

* [Azure Powershell](https://learn.microsoft.com/en-us/powershell/azure/install-az-ps?view=azps-9.2.0)
* [Azure CLI](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli)

### 2. Login

 login to azure on command line. Here we are doing for azure cli.

 ```bash
 az login
 A web browser has been opened at https://login.microsoftonline.com/organizations/oauth2/v2.0/authorize. Please continue the login in the web browser. If no web browser is available or if the web browser fails to open, use device code flow with `az login --use-device-code`.

 ```

 login on your browser and move to next step after you get output similar to following.

 ```json
    [
    {
        "cloudName": "AzureCloud",
        "homeTenantId": "6dc5ac9e-6d5f-98dh-bf37-78480f2d1b1f",
        "id": "0600d38a-5064-48c7-a6aa-92e4ebc788f9",
        "isDefault": true,
        "managedByTenants": [],
        "name": "Free Trial",
        "state": "Enabled",
        "tenantId": "6dc5ac9e-6d5f-48fc-bf37-78480f2d1b1f",
        "user": {
        "name": "vaibhav.kumar@knoldus.com",
        "type": "user"
        }
    }
    ]
 ```

* Note: it would be good if we configure the default location and default group, before creating resources.

```bash
az configure --defaults location=<location> 
az configure --defaults group=[resource group name]
```

### 3. Deployment of template on Azure

```bash
templateFile="azuredeploy.json"
today=$(date +"%d-%b-%Y")
DeploymentName="addoutputs-"$today

az deployment group create   --name $DeploymentName   --template-file $templateFile   --parameters storageSKU=Standard_LRS storageName=azureqwerty123
```

* Note: The storageName can be as per user requirement but should 3 to 14 characters long and only contain numbers and letters
