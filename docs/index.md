# Citrix Virtual Apps and Desktops 2112 SDK

> **Note:**
>
> Citrix Virtual Apps and Desktops was formerly XenApp and XenDesktop.
>
> The new product and component names stem from the expanding Citrix portfolio and cloud strategy.
Implementing this transition in our products and their documentation is an ongoing process.
Your patience during this transition is appreciated. For more detail about our new names, see <https://www.citrix.com/about/citrix-product-guide/>.

Citrix Virtual Apps and Desktops provide an SDK based on a number of Microsoft
Windows PowerShell version 3.0 cmdlets that allows you to perform the
same tasks as you would with the Citrix Studio console, together with
tasks you cannot do with Studio alone.

## Differences in policy rules

There are differences between the SDK and the Studio console in terms of
policy rules. Entitlement and assignment policy rules are independent
entities in the SDK; in the console, these entities are not visible as
they are seamlessly merged with the Delivery Group. Also, access policy
rules are less restrictive in the SDK.

## Use the SDK

The SDK comprises of a number of PowerShell cmdlets packaged both as modules and snap-ins. These are installed
automatically by the installation wizard when you install the Controller or Studio components.

To access and run the cmdlets:

1.  Start a shell in PowerShell 3.0.

    To start a shell from the console, click **Studio**, select the PowerShell tab, and click on **Launch PowerShell**.

    You must run the shell or script using an identity that has Citrix administration rights. Although members of the local administrators group on the Controller automatically have full administrative privileges to allow Citrix Virtual Apps and Desktops to be installed, Citrix recommends that for normal operation, you create Citrix administrators with the appropriate rights, rather than use the local administrators account.

1.  To use SDK cmdlets within scripts, set the execution policy in PowerShell. For more information about PowerShell execution policy, see your Microsoft documentation.

1.  To use this SDK through the snap-ins, add the snap-ins you require into the PowerShell environment using the **Add-PSSnapin** command in the Windows PowerShell console. **This step is unnecessary if you want to use the cmdlets in this SDK through the modules**.

    V1 and V2 denote the version of the snap-in (XenDesktop 7 snap-ins are version 2.).

    For example, type:

    `Add-PSSnapin Citrix.ADIdentity.Admin.V2`

    To import all the cmdlets, type:

    `Add-PSSnapin Citrix.\*.Admin.V\*`

    After importing, you have access to the cmdlets and their associated help.

    For an example of a typical use case, see [Get started with the SDK](./getting-started.md).