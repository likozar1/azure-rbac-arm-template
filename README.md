# azure-rbac-arm-template

## Template execution

```bash
$location = Read-Host -Prompt "Enter a location (i.e. centralus)"
[string[]]$actions = Read-Host -Prompt "Enter actions as a comma-separated list (i.e. action1,action2)"
$actions = $actions.Split(',')
$templateUri = "{template-url}"
New-AzDeployment -Location $location -TemplateUri $templateUri -actions $actions
```