# azure-rbac-arm-template

## Template execution

```bash
$location = Read-Host -Prompt "Enter a location (i.e. centralus)"
[string[]]$scopes = Read-Host -Prompt "Enter scopes as a comma-separated list (i.e. scope1,scope2)"
$scopes = $scopes.Split(',')
$templateUri = "https://raw.githubusercontent.com/likozar1/azure-rbac-arm-template/main/role-provision-template.json"
New-AzDeployment -Location $location -TemplateUri $templateUri -scopes $scopes
```