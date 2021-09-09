# Azure Data Explorer For Long Term Retention and KQL Query from Sentinel (Preview Script below)
# Create Azure Data Explorer (ADX) cluster, database and eventhub
```PowerShell
Connect-AzAccount
$projectName = Read-Host -Prompt "Enter a project name that is used for generating resource names"
$location = Read-Host -Prompt "Enter the location (i.e. centralus)"
$eventhubnamespace = $projectName + "-ehns"
$eventhubname = $projectName + "-eventhub
$resourceGroupName = "${projectName}rg"
$templateUri = "https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/quickstarts/microsoft.kusto/kusto-cluster-database/azuredeploy.json"
New-AzResourceGroup -Name $resourceGroupName -Location $location 
New-AzResourceGroupDeployment -ResourceGroupName $resourceGroupName -TemplateUri $templateUri
Write-Host "Press [ENTER] to continue ..."
New-AzEventHubNamespace -ResourceGroupName $resourceGroupName -NamespaceName namespace_name -Location eastus
New-AzEventHub -ResourceGroupName myResourceGroup -NamespaceName namespace_name -EventHubName $eventhubname -MessageRetentionInDays 3
Write-Host "Press [ENTER] to continue ..."
```
# Connect the new Eventhub to the Sentinel Log Analytics Workspace
```PowerShell
$TablesToBackup = "SigninLogs SecurityAlert Syslog"
az login
$Subscription = az account list-locations | Out-Gridview -passthrough
$RG = az group list --query "[?location=='eastus2']" | Out-gridview -passthrough
$SentinelWorkspace = az monitor log-analytics solution list --resource-group MyResourceGroup
$eventHubsNamespacesResourceId = '/subscriptions/$Subscription.Id/resourceGroups/$RG/providers/Microsoft.EventHub/namespaces/$SentinelWorkspace.name'
az monitor log-analytics workspace data-export create --resource-group $rg --workspace-name $SentinelWorkspace --name toEventHub --tables $TablesToBackup --destination $eventHubsNamespacesResourceId