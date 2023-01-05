# ARMtemplate
This is Azure Resource Manager (ARM) template file to provision storage in Azure Cloud. Using this, you can provision other resources on Azure as well.

```bash
templateFile="azuredeploy.json"
today=$(date +"%d-%b-%Y")
DeploymentName="addoutputs-"$today

az deployment group create   --name $DeploymentName   --template-file $templateFile   --parameters storageSKU=Standard_LRS storageName=azureqwerty123
```
* Note: The storageName can be as per user requirement but should 3 to 14 characters long and only contain numbers and letters