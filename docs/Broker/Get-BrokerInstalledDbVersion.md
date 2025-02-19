﻿
# Get-Brokerinstalleddbversion
Gets a list of all available database schema versions for the Broker Service.
## Syntax

```
Get-BrokerInstalledDbVersion [-Upgrade] [-Downgrade] [-AdminAddress <String>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```

## Detailed Description
Gets the current version number of the Citrix Broker Service database schema when called with no parameters.

When called with the -Upgrade parameter, gets the service schema version numbers to which an upgrade could be performed.

When called with the -Downgrade parameter, gets the service schema version numbers to which a downgrade could be performed.

The SQL scripts to perform schema upgrades and downgrades can be obtained using the Get-BrokerDBVersionChangeScript cmdlet. Citrix recommends that where possible service schema upgrades are performed using Studio rather than manually via the SDK.

Only one of the -Upgrade or -Downgrade parameters may be supplied at once.


## Related Commands

* [Get-BrokerDBVersionChangeScript](../Get-BrokerDBVersionChangeScript/)
* [Get-BrokerDBSchema](../Get-BrokerDBSchema/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Upgrade | Specifies that only schema versions to which the current database version can be updated should be returned. | false | false |  |
| Downgrade | Specifies that only schema versions to which the current database version can be reverted should be returned. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### System.Version
Get-BrokerInstalledDBVersion returns database schema version numbers as requested.
## Notes
If the command fails, the following errors can be returned.  
    Error Codes  
    -----------  
    InvalidParameterCombination  
        Both the Upgrade and Downgrade flags were specified.  
    NoOp  
        The operation was successful but had no effect.  
    NoDBConnections  
        The database connection string for the Broker Service has not been specified.  
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
    CommunicationError  
        There was a problem communicating with the remote service.  
    ExceptionThrown  
        An unexpected error occurred.  For more details, see the Windows event logs on the controller or the XenDesktop logs.
## Examples

### Example 1

```
C:\PS>Get-BrokerInstalledDBVersion
```

#### Description
Gets the current Citrix Broker Service database schema version number.
### Example 2

```
C:\PS>Get-BrokerInstalledDBVersion -Upgrade
```

#### Description
Get the versions of the Broker Service database schema for which upgrade scripts are supplied.
