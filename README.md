# Azure Logic Slack

This is an Azure logic app that you can use to parse Azure Monitor alerts that are using common alert schema and forward them to a Slack application. 

At this point it only handles `Platform` and `Smart Detector` (aka Smart Alert) but it can be extended fairly easily. 

At some point it would be nice to consolidate the workflow but this is a decent starting point. 


### Prep

1. Create a custom application on your slack server to get the webhook url.  
2. Update the parameters file to specify your slack webhook url and whatever you want to name the logic app



### Deploying the logic app

Make sure you're logged in first: 
`Connect-AzAccount`

Run the following commands in PowerShell:

`> $deploymentName = "slack-logic-app"`  
`> $resourceGroup = "rk-myresource"`  
`> $templateFile = "logic-slacknotification.json"`  
`> $templateParams = "logic-slacknotification.parameters.json"`  

```
> New-AzResourceGroupDeployment `
	-Name $deploymentName `
	-ResourceGroupName $resourceGroup `
  	-TemplateFile $templateFile `
  	-TemplateParameterFile $templateParams
```  	