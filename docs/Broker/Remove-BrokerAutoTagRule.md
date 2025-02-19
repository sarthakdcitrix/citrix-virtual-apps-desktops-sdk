﻿
# Remove-Brokerautotagrule
Removes an AutoTagRule.
## Syntax

```
Remove-BrokerAutoTagRule [-InputObject] <AutoTagRule[]> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [<CommonParameters>]  
  
Remove-BrokerAutoTagRule [-Name] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```

## Detailed Description
Removes an AutoTagRule.


## Related Commands

* [Get-BrokerAutoTagRule](../Get-BrokerAutoTagRule/)
* [New-BrokerAutoTagRule](../New-BrokerAutoTagRule/)
* [Set-BrokerAutoTagRule](../Set-BrokerAutoTagRule/)
* [Rename-BrokerAutoTagRule](../Rename-BrokerAutoTagRule/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the AutoTagRule to remove. | true | true (ByValue) |  |
| Name | The name of the AutoTagRule to remove. | true | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Autotagrule
AutoTagRules may be specified through pipeline input.
## Return Values

### None

## Examples

### Example 1

```
C:\PS> Remove-BrokerAutoTagRule -Name RandomAllocatedCatalogs
```

#### Description
Removes RandomAllocatedCatalogs AutoTagRule.
