# azure-rbac-arm-template

## Template execution

```bash
$location = Read-Host -Prompt "Enter a location (i.e. centralus)"
$templateUri = "https://raw.githubusercontent.com/likozar1/azure-rbac-arm-template/main/role-provision-template.json"
New-AzDeployment -Location $location -TemplateUri $templateUri
```