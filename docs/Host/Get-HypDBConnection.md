﻿
# Get-Hypdbconnection
Gets the database string for the specified data store used by the Host Service.
## Syntax

```
Get-HypDBConnection [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Returns the database connection string from the currently selected Host Service instance.

If the returned string is blank, no valid connection string has been specified. In this case the service is running, but is idle and awaiting specification of a valid connection string.

The current service instance is that on the local machine, or that explicitly specified by the last usage of the -AdminAddress parameter to a Host SDK cmdlet.


## Related Commands

* [Get-HypServiceStatus](../Get-HypServiceStatus/)
* [Set-HypDBConnection](../Set-HypDBConnection/)
* [Test-HypDBConnection](../Test-HypDBConnection/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### System.String
The database connection string configured for the current Host Service instance.
## Notes
If the command fails, the following errors can be returned.  
    Error Codes  
    -----------  
    NoDBConnections  
        The database connection string for the Host Service has not been specified.  
    PermissionDenied  
        You do not have permission to execute this command.  
    AuthorizationError  
        There was a problem communicating with the Citrix Delegated Administration Service.  
    CommunicationError  
        There was a problem communicating with the remote service.  
    ExceptionThrown  
        An unexpected error occurred.  For more details, see the Windows event logs on the controller or the XenDesktop logs.
## Examples

### Example 1

```
c:\PS>Get-HypDBConnection  
  
Server=serverName\SQLEXPRESS;Initial Catalog = databaseName;  Integrated Security = True
```

#### Description
Get the database connection string for the Host Service.
