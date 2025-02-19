﻿
# Get-Adminrole
Gets roles configured for this site.
## Syntax

```
Get-AdminRole [[-Name] <String>] [-Id <Guid>] [-BuiltIn <Boolean>] [-CanLaunchManage <Boolean>] [-CanLaunchMonitor <Boolean>] [-Description <String>] [-ExclusivePermission <String>] [-Metadata <String>] [-Permission <String>] [-Property <String[]>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-FilterScope <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Retrieves roles matching the specified criteria. If no parameters are specified, this cmdlet enumerates all roles.

See [about\_Admin\_Filtering](../about_Admin_Filtering/) for information about advanced filtering options.


## Related Commands

* [New-AdminRole](../New-AdminRole/)
* [Set-AdminRole](../Set-AdminRole/)
* [Rename-AdminRole](../Rename-AdminRole/)
* [Remove-AdminRole](../Remove-AdminRole/)
* [Set-AdminRoleMetadata](../Set-AdminRoleMetadata/)
* [Remove-AdminRoleMetadata](../Remove-AdminRoleMetadata/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | Gets roles with the specified name. | false | true (ByValue, ByPropertyName) |  |
| Id | Gets the role with the specified identifier. | false | true (ByPropertyName) |  |
| BuiltIn | Gets roles with the specified value of the BuiltIn flag. | false | false |  |
| CanLaunchManage | Gets roles with the specified value of the CanLaunchManage flag. | false | false |  |
| CanLaunchMonitor | Gets roles with the specified value of the CanLaunchMonitor flag. | false | false |  |
| Description | Gets roles with the specified description. | false | false |  |
| ExclusivePermission | Gets roles that contain a specific exclusive permission. | false | false |  |
| Metadata | Gets records with matching metadata entries.  
The value being compared with is a concatenation of the key name, a colon, and the value. For example: -Metadata "abc:x\*" matches records with a metadata entry having a key name of "abc" and a value starting with the letter "x". | false | false |  |
| Permission | Gets roles that contain a specific permission. | false | false |  |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| ReturnTotalRecordCount | When specified, the cmdlet outputs an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See [about\_Admin\_Filtering](../about_Admin_Filtering/) for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell-style filter expression. See [about\_Admin\_Filtering](../about_Admin_Filtering/) for details. | false | false |  |
| FilterScope | Gets only results allowed by the specified scope id. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Delegatedadmin.Sdk.Role
Get-AdminRole returns an object for each matching role.
## Examples

### Example 1

```
C:\PS> Get-AdminRole -Id 20852cdf-f527-4953-ba6e-e7545217122d
```

#### Description
Gets the details of the role with the specific id.
### Example 2

```
C:\PS> Get-AdminRole -BuiltIn $false
```

#### Description
List all custom roles.
