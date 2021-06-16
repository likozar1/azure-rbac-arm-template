# azure-rbac-arm-template

## Template execution2

### Execute Role template

```bash
[string[]]$scopes = Read-Host -Prompt "Enter scopes as a comma-separated list (i.e. scope1,scope2)"
$scopes = $scopes.Split(',')
$hub = Read-Host -Prompt "Enter IoT Hub scope name (i.e. IoT hub name)"
$resourceGroupName = az iot hub show --name $hub --query "resourcegroup" --output tsv
$templateUri = "https://raw.githubusercontent.com/likozar1/azure-rbac-arm-template/main/role-provision-template.json"
New-AzResourceGroupDeployment -ResourceGroupName $resourceGroupName -TemplateUri $templateUri -scopes $scopes
```

### Execute RoleAssignent template:

```bash
$hub = Read-Host -Prompt "Enter IoT Hub scope name (i.e. IoT hub name)"
$resourceGroupName = az iot hub show --name $hub --query "resourcegroup" --output tsv
$templateUri = "https://raw.githubusercontent.com/likozar1/azure-rbac-arm-template/main/role-assignment-template.json"
New-AzResourceGroupDeployment -ResourceGroupName $resourceGroupName -TemplateUri $templateUri -scope $hub
```

### Execute Nested Role and Assignment template:

```bash
$hub = Read-Host -Prompt "Enter IoT Hub scope name (i.e. IoT hub name)"
$principalName = Read-Host -Prompt "Enter Principal scope name (i.e. principal name)"
$principalId = az ad sp list --display-name $principalName --query "[].objectId" --output tsv
$resourceGroupName = az iot hub show --name $hub --query "resourcegroup" --output tsv
$templateUri = "https://raw.githubusercontent.com/likozar1/azure-rbac-arm-template/main/role-provision-template-nested.json"
New-AzResourceGroupDeployment -ResourceGroupName $resourceGroupName -TemplateUri $templateUri -scope $hub -principalId $principalId
```
