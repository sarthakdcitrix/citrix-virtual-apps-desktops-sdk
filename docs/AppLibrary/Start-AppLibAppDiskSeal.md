﻿
# Start-Applibappdiskseal
Seals an AppDisk in the Application library service
## Syntax

```
Start-AppLibAppDiskSeal [-AppDiskName] <String> [-SkipAppDnaAnalysis] [-RunAsynchronously] [-PurgeJobOnSuccess] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]  
  
Start-AppLibAppDiskSeal -AppDiskUid <Guid> [-SkipAppDnaAnalysis] [-RunAsynchronously] [-PurgeJobOnSuccess] [-LoggingId <Guid>] [-BearerToken <String>] [-TraceParent <String>] [-TraceState <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
Lets you mark an AppDisk with installed applications as ready for use.


## Related Commands

* [Get-AppLibTask](../Get-AppLibTask/)
* [New-AppLibAppDisk](../New-AppLibAppDisk/)
* [Set-AppLibAppDisk](../Set-AppLibAppDisk/)
* [Get-AppLibAppDisk](../Get-AppLibAppDisk/)
* [Import-AppLibAppDisk](../Import-AppLibAppDisk/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AppDiskName | The name of the AppDisk to seal. | true | false |  |
| AppDiskUid | The Uid of the AppDisk to seal | true | true (ByPropertyName) |  |
| SkipAppDnaAnalysis | Indicates that AppDNA analysis of the AppDisk should be skipped. | false | false | false |
| RunAsynchronously | Indicates whether or not the command returns before it is complete. If specified, the command returns an identifier for the task that was created. This task can be monitored using the Get-AppLibTask command. | false | false | false |
| PurgeJobOnSuccess | Indicates that the task history is removed from the database when the task has finished. This can only be specified for tasks that are not run asynchronously. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| TraceParent | Specifies the trace parent assigned for internal diagnostic tracing use | false | false |  |
| TraceState | Specifies the trace state assigned for internal diagnostic tracing use | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### System.Guid
When the RunAsynchronously identifier is specified, this GUID is returned and provides the task identifier
### System.Management.Automation.Pscustomobject
System.Management.Automation.PSCustomObject This object provides details of the task that was run and contains the following information:  
TaskId &lt;Guid&gt; The identifier for the task that was performed. Active &lt;Boolean&gt; Indicates whether the task is still processing or is complete. Host &lt;string&gt; The name of the host on which the task is running or was run. DateStarted &lt;DateTime&gt; The date and time that the task was initiated. LastUpdateTime &lt;DateTime&gt; The date and time of the last task status update DateFinished &lt;DateTime&gt; The date and time that the task finished execution Metadata &lt;Metadata\[\]&gt; Associated key-value data TaskState &lt;string&gt; Where in its lifecycle the task is CurrentOperation &lt;string&gt; Operation specific phase of the overall "Running" task state. TerminatingError &lt; Citrix.Fma.Sdk.ServiceCore.CommonCmdlets.TaskterminatingError&gt; Diagnostic information in the case of a complete task failure ActiveElapsedTime &lt;int&gt; How many seconds of active execution the task has taken Type &lt;string&gt; The type of task. For this cmdlet's tasks, this is always SealAppDisk. AppDiskName &lt;string&gt; The name of the AppDisk that the task was for. AppDiskUid &lt;string&gt; The identifier of the AppDisk that the task was for. TaskStateInformation &lt;string&gt; Additional information about the current task state. TaskProgress &lt;double&gt; The progress of the task 0-100%. DiskLocalUid &lt;Guid&gt; The identifier of the AppDisk lineage. DiskLocalVersion &lt;Guid&gt; The identifier of the AppDisk within its lineage. RemoteTaskId &lt;Guid&gt; The identifier of the associated disk management task on the Machine Creation Service HostingUnitName &lt;string&gt; The name of the associated hosting unit HostingUnitUid &lt;Guid&gt; The indentifier of the associated hosting unit VirtualDiskId &lt;Guid&gt; The identifier of the AppDisk stack DiskId &lt;string&gt; The hypervisor's identifier for the disk being imported RunAppDnaAnalysis &lt;bool&gt; Whether AppDNA analysis has been run LayerSealingProgress &lt;int&gt; A percentage measure of the progress ReservedMachineSid  &lt;string&gt; The machine previously reserved when the AppDisk was first created
## Notes
Only one long-running task for each AppDisk can be processed at a time.  
    In case of failure, the following errors can result.  
    Error Codes  
    -----------  
    JobCreationFailed  
    The requested task could not be started.  
    DatabaseError  
    An error occurred in the service while attempting a database operation.  
    DatabaseNotConfigured  
    The operation could not be completed because the database for the service is not configured.  
    ServiceStatusInvalidDb  
    An error occurred in the service while attempting a database operation. Communication with the database failed for  
    for various reasons.  
    CommunicationError  
    An error occurred while communicating with the service.  
    InvalidParameterCombination  
    Both PurgeJobOnSuccess and RunAsynchronously were specified. When running asynchronously, the cmdlet terminates before the job does, so it cannot clean up the completed job.  
    PermissionDenied  
    The user does not have administrative rights to perform this operation.  
    ConfigurationLoggingError  
    The operation could not be performed because of a configuration logging error.  
    ExceptionThrown  
    An unexpected error occurred. To locate more details, see the Windows event logs on the controller being used, or examine the XenDesktop logs.
## Examples

### Example 1

```
C:\PS>Start-AppLibAppDiskSeal -AppDiskName "AppDiskName" -SkipAppDnaAnalysis  
  
          TaskId                              : 90e93b9d-a225-4701-ad50-fa1546af35ac  
  
          AppDiskName                         : MyAppDisk  
  
          AppDiskUid                          : d9ba6487-05f8-48ad-a178-1794605e2b8e  
  
          Active                              : False  
  
          DiskLocalUid                        : 7b4c01c4-72fa-4c80-913d-c6df785f4297  
  
          DiskLocalVersion                    : 25118c6e-a737-4fb9-b4b3-121910a73160  
  
          DateStarted                         : 17/11/2015 09:15:22  
  
          LastUpdateTime                      : 17/11/2015 09:43:18  
  
          DateFinished                        : 17/11/2015 09:43:18  
  
          Type                                : SealAppDisk  
  
          Metadata                            : {}  
  
          TaskState                           : Finished  
  
          TaskStateInformation                :  
  
          TaskProgress                        : 100  
  
          TerminatingError                    :  
  
          HostingUnitName                     : XenHU  
  
          HostingUnitUid                      : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501  
  
          Host                                : MyHost  
  
          VirtualDiskId                       : 7ce3c9a5-2888-45ba-8629-398f9e4eba7d  
  
          CurrentOperation                    :  
  
          ActiveElapsedTime                   : 1676  
  
          ReservedMachineSid                  : S-1-5-21-2316621082-1546847349-2782505528-1165  
  
          LayerSealingProgress                : 100  
  
          RunAppDnaAnalysis                   : False
```

#### Description
Seals the AppDisk with the name "AppDiskName"
### Example 2

```
C:\PS>Start-AppLibAppDiskSeal -AppDiskUid $AppDiskUid  -RunAsynchronously  
  
          Guid  
  
          ----  
  
          6dd85fec-96cf-46b1-9cd4-d8ba7d06e85b
```

#### Description
Seal the AppDisk with the Uid \$AppDiskUid asynchronously. To get the task details, use Get-AppLibTask -TaskID &lt;task id&gt;  
i.e.  
C:\\PS&gt;Get-AppLibTask -TaskID 6dd85fec-96cf-46b1-9cd4-d8ba7d06e85b  
TaskId                              : 6dd85fec-96cf-46b1-9cd4-d8ba7d06e85b AppDiskName                         : MyUpdatedAppDisk AppDiskUid                          : 3b9c6b62-be1e-467b-9cb4-025ad9cba916 Active                              : False DiskLocalUid                        : 7b4c01c4-72fa-4c80-913d-c6df785f4297 DiskLocalVersion                    : a23f8bae-dedf-433f-8908-025144ff4f81 DateStarted                         : 17/11/2015 09:15:22 LastUpdateTime                      : 17/11/2015 09:43:18 DateFinished                        : 17/11/2015 09:43:18 Type                                : SealAppDisk Metadata                            : {} TaskState                           : Finished TaskStateInformation                : TaskProgress                        : 100 TerminatingError                    : HostingUnitName                     : XenHU HostingUnitUid                      : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501 Host                                : MyHost VirtualDiskId                       : 4c245ff7-5cdd-4aac-a854-1e101e23d1f6 CurrentOperation                    : ActiveElapsedTime                   : 1676 ReservedMachineSid                  : S-1-5-21-2316621082-1546847349-2782505528-1165 LayerSealingProgress                : 100 RunAppDnaAnalysis                   : False
