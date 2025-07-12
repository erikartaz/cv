---
title: "A Day in the Life of an Azure FinOps Practitioner"
date: 2025-07-12T15:55:23+02:00
draft: false
toc: false
images:
tags:
  - Azure
  - Cloud
  - Blog
  - FinOps
---

Every day in Azure FinOps feels like navigating a massive, ever-evolving financial control tower in the cloud. My mornings usually start with dashboards—lots of dashboards. I check daily cost trends, unusual spikes, and usage anomalies across subscriptions and resource groups. It's like being a financial detective with access to telemetry and APIs.

Next comes tagging hygiene and resource governance. Are our cost allocation tags consistent? Have new untagged resources appeared overnight? If yes, it's time to engage with resource owners or automate fixes. Clean data is the foundation of good decisions.

By mid-morning, I’m often deep into analyzing consumption patterns: spotting idle virtual machines, underutilized PaaS services, or forgotten public IPs. These small things add up—so I identify optimization opportunities and feed them into monthly reports or real-time recommendations.

Afternoons are for collaboration. I work closely with app teams, finance, and cloud architects. Together, we assess Azure Reservations or Savings Plans, align budgets with forecasts, and simulate changes before committing. Often, this means scripting simulations (hello PowerShell and REST APIs) or pulling cost data into Power BI for clearer storytelling.

What I love most is that FinOps isn’t just about saving money. It’s about creating visibility, fostering accountability, and helping teams make smart, data-driven decisions in the cloud. Every day brings new insights—and new chances to bring clarity to the cloud chaos.


```powershell {style=onedark}

Connect-AzAccount

$sublist= Get-AzSubscription 
foreach ($item in $sublist){

$scopeappend= "/subscriptions/"+$item.Id
$export=(Get-AzRoleAssignment -RoleDefinitionId "8e3af657-a8ff-443c-a75c-2fe8c4bcb635" -Scope $tdt  | where {($_.ObjectType -EQ "user") -and ($_.Scope -EQ $scopeappend) }  ) | select DisplayName,SignInName
}

$export|Export-Csv -Path C:\test.csv
```
