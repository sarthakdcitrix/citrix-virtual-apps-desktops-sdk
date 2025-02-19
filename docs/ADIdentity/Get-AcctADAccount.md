﻿
# Get-Acctadaccount
Gets the AD accounts stored in the AD Identity Service.
## Syntax

```
Get-AcctADAccount [-IdentityPoolName <String>] [-ADAccountSid <String>] [-Domain <String>] [-State <ADIdentityState>] [-Lock <Boolean>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-FilterScope <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]  
  
Get-AcctADAccount [-IdentityPoolUid <Guid>] [-ADAccountSid <String>] [-Domain <String>] [-State <ADIdentityState>] [-Lock <Boolean>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-FilterScope <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Provides the ability to locate the AD accounts stored within the AD Identity Service and view the state of the accounts.


## Related Commands

* [New-AcctADAccount](../New-AcctADAccount/)
* [Add-AcctADAccount](../Add-AcctADAccount/)
* [Remove-AcctADAccount](../Remove-AcctADAccount/)
* [Unlock-AcctADAccount](../Unlock-AcctADAccount/)
* [Update-AcctADAccount](../Update-AcctADAccount/)
* [Repair-AcctADAccount](../Repair-AcctADAccount/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ADAccountSid | The AD Account SID of the account. | false | false |  |
| Domain | The domain of the account (this is in dns format). | false | false |  |
| State | The current state of the identity stored in the AD Identity Service for the AD account. | false | false |  |
| Lock | Indicates if the account is locked in the AD Identity Service. | false | false |  |
| ReturnTotalRecordCount | See [about\_Acct\_Filtering](../about_Acct_Filtering/) for details. | false | false | false |
| MaxRecordCount | See [about\_Acct\_Filtering](../about_Acct_Filtering/) for details. | false | false | 250 |
| Skip | See [about\_Acct\_Filtering](../about_Acct_Filtering/) for details. | false | false | 0 |
| SortBy | See [about\_Acct\_Filtering](../about_Acct_Filtering/) for details. | false | false |  |
| Filter | See [about\_Acct\_Filtering](../about_Acct_Filtering/) for details. | false | false |  |
| FilterScope | Gets only results allowed by the specified scope id. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |
| IdentityPoolName | The name of the identity pool to which the account is registered. | false | true (ByPropertyName) |  |
| IdentityPoolUid | The unique identifier for the identity pool that the account is registered to. | false | false |  |

## Input Type

### 

## Return Values

### Citrix.Adidentity.Sdk.Identityinpool
The Get-AcctADAccount returns an object that contains the following parameters  
        ADAccountSid &lt;string&gt;  
            The AD account SID for the retrieved account.  
        ADAccountName &lt;string&gt;  
          The AD account name for the retrieved account.  
          Domain &lt;string&gt;  
            The domain for the imported account.  
        State &lt;Citrix.XDInterServiceTypes.ADIdentityState&gt;  
            The state for the account. This can be;  
                Available  
                    The account is not used.  
                InUse  
                    The account is in use.  
                Error  
                    The account is in error (i.e. the account is locked or disabled in AD).  
                Tainted  
                     The account is no longer used, but the password is no longer known.  
        Lock &lt;Boolean&gt;  
            The account is locked (in the database not in AD).  
        IdentityPoolName &lt;System.String&gt;  
            The name of the containing identity pool.  
        IdentityPoolUid &lt;System.Guid&gt;  
            The GUID identifying the containing identity pool.
## Notes
In the case of failure the following errors can result.  
    Error Codes  
    -----------  
    PartialData  
    Only a subset of the available data was returned.  
    CouldNotQueryDatabase  
    The query required to get the database was not defined.  
    PermissionDenied  
    The user does not have administrative rights to perform this operation.  
    ConfigurationLoggingError  
    The operation could not be performed because of a configuration logging error  
    CommunicationError  
    An error occurred while communicating with the service.  
    DatabaseNotConfigured  
    The operation could not be completed because the database for the service is not configured.  
    InvalidFilter  
    A filtering expression was supplied that could not be interpreted for this cmdlet.  
    ExceptionThrown  
    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1

```
C:\>Get-AcctADAccount
```

#### Description
Return all the AD accounts that are registered in the AD Identity Service.
### Example 2

```
C:\>Get-AcctADAccount -IdentityPoolName MyPool -Lock $false
```

#### Description
Return all the AD accounts that are registered in the AD Identity Service in the identity pool called "MyPool" that are also locked.
### Example 3

```
C:\>Get-AcctADAccount -Filter {IdentityPoolName -Like "p\*" -or IdentityPoolName -eq "MyPool"}
```

#### Description
Return all the AD accounts that are registered in the AD Identity Service in the identity pool called "MyPool" or in an identity pool that has a name that starts with a 'p'.  For full details of the advanced filtering aspects of this command see [about\_Acct\_Filtering](../about_Acct_Filtering/).
