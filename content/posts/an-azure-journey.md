---
title: "An Azure Journey"
date: 2025-07-12T15:55:23+02:00
draft: false
toc: false
images:
tags:
  - Azure
  - Cloud
  - Blog
---

### Questo è il primo post

Vediamo cosa possiamo scrivere e sopratutto quanto sarà larga la pagina, perché questa è una parte veramente molto importante in modo da capire l'effetto.

Adesso andiamo a capo
ancora a capo. ma senza stacco

Vediamo ora un po' di codice

```powershell {style=onedark}

Connect-AzAccount

$sublist= Get-AzSubscription 
foreach ($item in $sublist){

    $scopeappend= "/subscriptions/"+$item.Id
$export=(Get-AzRoleAssignment -RoleDefinitionId "8e3af657-a8ff-443c-a75c-2fe8c4bcb635" -Scope $tdt  | where {($_.ObjectType -EQ "user") -and ($_.Scope -EQ $scopeappend) }  ) | select DisplayName,SignInName
}

$export|Export-Csv -Path C:\test.csv
```
