﻿
# Set-Provserviceconfigurationdata
Sets the value for the given key in the service configuration data.
## Syntax

```
Set-ProvServiceConfigurationData [-Name] <String> -Value <String> [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Provides the ability for additional custom data to be stored for the MachineCreation Service.


## Related Commands

* [Remove-ProvServiceConfigurationData](../Remove-ProvServiceConfigurationData/)
* [Get-ProvServiceConfigurationData](../Get-ProvServiceConfigurationData/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | Specifies the key name of the metadata to be added.  The key must be unique.  
The Name cannot contain any of the following characters \\/;:#.\*?=&lt;&gt;|\[\]()""' | true | false |  |
| Value | Specifies the value for the name.  If the name already exists, its value is updated. | true | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Machinecreation.Sdk.Serviceconfigurationdata
Set-ProvServiceConfigurationData returns an object containing the new definition of the configuration.  
    Name &lt;string&gt;  
        Specifies the name for the item of data.  
    Value &lt;string&gt;  
        Specifies the value of the data.
## Notes
In the case of failure the following errors can be produced.  
    Error Codes  
    -----------  
    DatabaseError  
        An error occurred in the service while attempting a database operation.  
    DatabaseNotConfigured  
        The operation could not be completed because the database for the service is not configured.  
    DataStoreException  
        An error occurred in the service while attempting a database operation - communication with the database failed for various reasons.  
    PermissionDenied  
        You do not have permission to execute this command.  
    AuthorizationError  
        There was a problem communicating with the Citrix Delegated Administration Service.  
    ConfigurationLoggingError  
        The operation could not be performed because of a configuration logging error.  
    CommunicationError  
        An error occurred while communicating with the service.  
    ExceptionThrown  
        An unexpected error occurred.  To locate more details see the Windows event logs on the controller being used, or examine the XenDesktop logs.
## Examples

### Example 1

```
C:\PS>Set-ProvServiceConfigurationData -Name "customProperty1" -Value "value2"  
  
Name                            Value  
  
--------                        -----  
  
customProperty1                 value2
```

#### Description
Set data with a name of 'customProperty1' and value of 'value2' to the service configuration.
