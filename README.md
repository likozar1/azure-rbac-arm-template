# azure-rbac-arm-template

## Template execution2

### Execute Role template

```bash
[string[]]$scopes = Read-Host -Prompt "Enter scopes as a comma-separated list (i.e. scope1,scope2)"
$scopes = $scopes.Split(',')
$resourceGroupName = "gator-iota-hub-rg"
$templateUri = "https://raw.githubusercontent.com/likozar1/azure-rbac-arm-template/main/role-provision-template.json"
New-AzResourceGroupDeployment -ResourceGroupName $resourceGroupName -TemplateUri $templateUri -scopes $scopes
```

### Execute RoleAssignent template:

```bash
$scope = Read-Host -Prompt "Enter assignment scope (i.e. iot hub ID)"
$resourceGroupName = "gator-iota-hub-rg"
$templateUri = "https://raw.githubusercontent.com/likozar1/azure-rbac-arm-template/main/role-assignment-template.json"
New-AzResourceGroupDeployment -ResourceGroupName $resourceGroupName -TemplateUri $templateUri -scope $scope
```


$scope = Read-Host -Prompt "Enter assignment scope (i.e. iot hub ID)"
$resourceGroupName = "gator-iota-hub-rg"
$templateUri = "https://raw.githubusercontent.com/likozar1/azure-rbac-arm-template/main/role-provision-template-nested.json"
New-AzResourceGroupDeployment -ResourceGroupName $resourceGroupName -TemplateUri $templateUri -scope $scope