﻿
# Get-Logdbversionchangescript
Gets an SQL service schema update script for the Citrix ConfigurationLogging Service.
## Syntax

```
Get-LogDBVersionChangeScript -DatabaseName <String> -TargetVersion <Version> [-DataStore <String>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Gets an SQL script that can be used to update the current Citrix ConfigurationLogging Service database schema. An update can be an upgrade or downgrade.

A script can be obtained to update the current service schema to any version that is reachable by applying available schema update packages that have been uploaded by the Citrix ConfigurationLogging Service.

Typically, this mechanism is used to update the current service schema to a newer version, however it can also be used to revert previously applied updates.

The SQL script obtained can be run using SQL Server's SQLCMD utility, or by copying the script into an SQL Server Management Studio (SSMS) query window and executing the query. If using SSMS, the query must be executed in 'SQLCMD mode'.

The schema update packages used to generate update scripts are stored in the database; because of this, any Citrix ConfigurationLogging Service in the site can be used to obtain a schema update script.

The fact that an update package is available in the database does not mean that the update has actually been applied to the service's schema. In addition, application of an update does not remove the associated update packages.

Take care when using the update scripts. Citrix recommends that where possible service schema upgrades are performed using Studio rather than manually via the SDK. The database should be backed-up before an update is attempted. The database script may also require exclusive use of the schema, in which case all Citrix ConfigurationLogging Services must be shutdown before applying the update.

Once an update has been applied to the service schema, any existing Citrix ConfigurationLogging Services that are incompatible with the updated schema will cease to operate. The service state, as reported by Get-LogServiceStatus, provides information about the service compatibility (e.g. DBNewerVersionThanService).


## Related Commands

* [Get-LogInstalledDBVersion](../Get-LogInstalledDBVersion/)
* [Get-LogServiceStatus](../Get-LogServiceStatus/)
* [Get-LogDBSchema](../Get-LogDBSchema/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| DatabaseName | The name of the database containing the Citrix ConfigurationLogging Service schema to be updated. | true | false |  |
| TargetVersion | The required target service schema version of the update. This is the service schema version obtained after the update script is applied. | true | false |  |
| DataStore | Specifies the logical name of the data store for the ConfigurationLogging Service. Can be either be 'Site' or the logical name of the secondary data store. | false | false | Site |
| BearerToken | Specifies the bearer token assigned to the calling user. | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site id the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### System.Management.Automation.Psobject
The Get-LogDBVersionChangeScript cmdlet returns a PSObject containing a script that can be used to update the Citrix ConfigurationLogging Service database schema. The object has the following properties:  
-- Script  
The raw text of the SQL script to apply the update, or null in the case when no upgrade path to the specified target version exists.  
-- CanUndo  
If true, indicates that after the update has been applied, a script to revert from the updated schema to the schema state prior to the update can be obtained. Because Get-LogDBVersionChangeScript gets only update scripts relating to the current schema version, a script to revert an update can be obtained only after the update has been applied.  
-- NeedExclusiveAccess  
If true, indicates that the update requires exclusive access to the Citrix ConfigurationLogging Service's schema while the update is applied; all Citrix ConfigurationLogging Services must be shutdown during the update.
## Notes
Scripts to update the schema version are stored in the database so any service in the service group can obtain these scripts. Extreme caution should be exercised when using update scripts. Citrix recommends backing up the database before attempting to upgrade the schema.  Database update scripts may require exclusive use of the schema and so may not be able to execute while any ConfigurationLogging services are running.  However, this depends on the specific update being carried out.  
    After a schema update has been carried out, services that require the previous version of the schema may cease to operate.  The ServiceState parameter reported by the Get-LogServiceStatus command provides information about service compatibility.  For example, if the schema has been upgraded to a more recent version that a service cannot use, the service reports "DBNewerVersionThanService".  
    If the command fails, the following errors can be returned.  
    Error Codes  
    -----------  
    NoOp  
        The operation was successful but had no effect.  
    NoDBConnections  
        The database connection string for the ConfigurationLogging Service has not been specified.  
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
C:\PS> $update = Get-LogDBVersionChangeScript -DatabaseName MyDb -TargetVersion 1.0.75.0  
  
C:\PS> $update.Script > update_75.sql
```

#### Description
Gets an SQL update script to update the current schema to version 1.0.75.0. The resulting update\_75.sql script is suitable for direct use with the SQL Server SQLCMD utility.
