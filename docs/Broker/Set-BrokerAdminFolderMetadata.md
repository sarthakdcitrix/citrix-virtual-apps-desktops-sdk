﻿
# Set-Brokeradminfoldermetadata
Creates/Updates metadata key-value pairs for AdminFolder
## Syntax

```
Set-BrokerAdminFolderMetadata [-AdminFolderId] <Int32> -Name <String> -Value <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [<CommonParameters>]  
  
Set-BrokerAdminFolderMetadata [-AdminFolderId] <Int32> -Name <String> -Value <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [<CommonParameters>]  
  
Set-BrokerAdminFolderMetadata [-AdminFolderId] <Int32> -Map <PSObject> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [<CommonParameters>]  
  
Set-BrokerAdminFolderMetadata [-InputObject] <AdminFolder[]> -Name <String> -Value <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [<CommonParameters>]  
  
Set-BrokerAdminFolderMetadata [-InputObject] <AdminFolder[]> -Map <PSObject> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [<CommonParameters>]  
  
Set-BrokerAdminFolderMetadata [-AdminFolderName] <String> -Name <String> -Value <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [<CommonParameters>]  
  
Set-BrokerAdminFolderMetadata [-AdminFolderName] <String> -Map <PSObject> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```

## Detailed Description
The Set-BrokerAdminFolderMetadata cmdlet creates/updates metadata key-value pairs for AdminFolder. The AdminFolder can be specified by InputObject or piping.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminFolderId | Specifies the AdminFolder object whose Metadata is to be created/updated by ID. | true | true (ByValue) |  |
| InputObject | Specifies the AdminFolder objects whose Metadata is to be created/updated. | true | true (ByValue) |  |
| AdminFolderName | Specifies the AdminFolder object whose Metadata is to be created/updated by name. | true | true (ByValue, ByPropertyName) |  |
| Name | Specifies the name of the Metadata member to be created/updated | true | true (ByPropertyName) |  |
| Value | Specifies the value of the Metadata member to be created/updated | true | true (ByPropertyName) |  |
| Map | Specifies a hashtable containing name/value pairs to be used to create or update Metadata members | true | true (ByValue) |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Brokeradminfolder
You can pipe the AdminFolder to hold the new or updated metadata.
## Return Values

### None Or Citrix.Broker.Admin.Sdk.Brokeradminfolder
This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.BrokerAdminFolder object.
## Examples

### Example 1

```
C:\PS> Set-BrokerAdminFolderMetadata -InputObject $obj-Uid -Name "MyMetadataName" -Value "1234"
```

#### Description
This command creates/updates the Metadata "MyMetadataName" key-value pair for the AdminFolder whose instance is pointed by \$obj-Uid
### Example 2

```
C:\PS> Get-BrokerAdminFolder | Set-BrokerAdminFolderMetadata -Name "MyMetadataName" -Value "1234"
```

#### Description
This command creates/updates metadata key "MyMetadataName" with the value "1234" for all the AdminFolder in the site
### Example 3

```
C:\PS> @{ 'name1' = 'value1'; 'name2' = 'value2' } | Set-BrokerAdminFolderMetadata 'objname'
```

#### Description
This command creates/updates two metadata keys "name1" and "name2" with the values "value1" and "value2" respectively for the AdminFolder in the site whose name is 'objname'
