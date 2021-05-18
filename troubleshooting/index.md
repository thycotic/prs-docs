[title]: # (Troubleshooting)
[tags]: # (Troubleshooting)
[priority]: # (950)

# Troubleshooting

## SQL Server Encryption

Administrators can enable end-to-end encryption with the SQL database by using an Encrypted connection. This is a feature that is built into Microsoft SQL Server and Password Reset Server supports. It can be enabled in the 2nd step of the installer by checking the "Enable Encryption" check box.

SQL Server must be pre-configured to support encryption. This Microsoft TechNet article explains how to configure the SQL Server environment for encryption:

<http://technet.microsoft.com/en-us/library/ms191192.aspx>

## SQL Login Fails Suddenly

__Login failed for user__

A severe error occurred on the current command.  The results, if any, should be discarded.

Description: An unhandled exception occurred during the execution of the current web request. Please review the stack trace for more information about the error and where it originated in the code.

Exception Details: System.Data.SqlClient.SqlException: Login failed for user. A severe error occurred on the current command.  The results, if any, should be discarded.

This sudden failure may be because the "Enforce Password Expiration" setting is turned on for the SQL Login Account for Secret Server.  In SQL Server Management Studio, turn off this setting by right clicking and selecting "Properties" on the user under the "Security\Logins" folder.  On the properties page, uncheck the "Enforce password expiration" checkbox and save.

### Performance issues

Note that using this setting can adversely affect performance.
<http://technet.microsoft.com/en-us/library/ms189067.aspx>

## Backup Configuration File Path Settings

There are two file path settings on the Admin > Backup page (ConfigurationBackup.aspx). The "Backup File Path" setting corresponds to the application backup. The "Backup Database Path" setting corresponds to the SQL server backup.

Generally, the "Backup File Path" setting can be set to a path local to the application server for backing up of application files. If Secret Server is running under an account that does not have permission to write to a local path, then a network share can be used.

If the SQL server is located on the same server as the web application server, the "Backup Database File Path" setting can be set to a local path. If the SQL server is not located on the same server as the web application server then a network share should be used. The account under which SQL server service is running either must have modify rights to that path or must be a member of a group with modify rights to that path. You must use UNC (Universal Naming Convention) notation to write to a network path (ie. \\TESTVM0\c$\backupDirectory).

If you are getting an error stating "Cannot open backup device. Operating system error 3", this is often due to an invalid path value.

## Troubleshooting Database Timeout

If you see an error similar to below, then the machine running Password Reset Server is having trouble using the Password Reset Server database:

This error is caused when Password Reset Server tries to a run a database query, but the query times out before completion. To diagnose the issue, please follow these steps:

* Check the task manager on the machine running your Password Reset Server database. Make sure no process is taking up too much ram or CPU power. If it is, stop the process or move the Password Reset Server database to another machine.

* Check the hard drive space on the machine running your Password Reset Server database. Make sure there is at least 3 gigabytes of free space.

* Try restarting the SQL Service.

## Setting up Password Reset Server for disaster recovery

Password Reset Server supports setting up the database in a disaster recovery environment by using Microsoft SQL AlwaysOn or the mirroring capabilities in SQL Server 2005 and SQL Server 2008. This allows you to have a copy of your Password Reset Server database on another server and automatically start using the backup server should your primary database server fail.

Click [here](https://my.thycotic.com/articles/secretserver/SQLServerMirroringAndSSL.pdf) for a detailed guide to configuring Password Reset Server for database mirroring:

## Enabling WMI ports on Windows client machines

### Windows 7

* Run services.msc and ensure Windows "Management Instrumentation" service Startup Type is set to Automatic.

* In Firewall settings, click on the "Advanced settings" link. For the Inbound Rules, ensure "Windows Management Instrumentation (WMI-In)" is Enabled and Allowed for the Profile called Domain.

### Vista

* Run services.msc and ensure "Windows Management Instrumentation" service Startup Type is set to Automatic.

* In Firewall settings, click on the "Change Settings" link. In the Windows Firewall Settings dialog, click the Exceptions tab. Enable the "Windows Management Instrumentation (WMI)" exception.

### Windows XP

* Run services.msc and ensure "Windows Management Instrumentation" service Startup Type is set to Automatic.

* From the command prompt, run the following command: "netsh firewall set service RemoteAdmin enable"

* From the command prompt, run the following command: "netsh firewall add portopening protocol=tcp port=135 name=DCOM_TCP135"

* From the command prompt, run the following command: "netsh firewall set portopening tcp 445 smb enable"

## Why are some user email addresses blank?

In Password Reset Server, email addresses used for password expiration notifications and enrollment reminders are retrieved from Active Directory. When you enter a domain and perform a synchronization, Password Reset Server will create all users that exist in AD and use their AD email addresses. If an email address in Password Reset Server appears as blank, this means the email address is also blank in Active Directory.

To fix this, an administrator can edit the user in Active Directory, add an email address, and then force a synchronization or wait for a scheduled synchronization to occur. To force synchronization in PRS, an admin can log in through the web portal, click on "Administration", then on "Domain Configuration", and click "Synchronize Now".

## HttpException Maximum request length exceeded error

This error occurs when too much data is sent to the server on a request. This can be caused by a large file attachment.

To fix this, first locate the page on which this occurred. Then, edit the web.config file that exists in your Password Reset Server installation directory. Next, search for the <location> tag that contains the page on which the error occurred. For example, if you received this error on the CreateUser.aspx, you would want to look for the following section:

```
<location path="CreateUser.aspx">
        <system.web>
            <authorization>
                <allow users="*"/>
            </authorization>
        </system.web>
</location>

```

If you located the tag, then add the following line directly above the closing </system.web> tag:

```

<httpRuntime maxRequestLength="20480" executionTimeout="600" />

```

So, in this case, your CreateUser node should look like this:

```
<location path="CreateUser.aspx">
        <system.web>
            <authorization>
                <allow users="*"/>
            </authorization>
            <httpRuntime maxRequestLength="20480" executionTimeout="600" />
        </system.web>
</location>

```

In some cases, this tag may not exist in your web.config file. When this occurs, create a new section right before the closing </configuration> in the file. This closing tag usually is on the last line of the file. For example, if you received the error on DomainSynchronize.aspx, add the following lines to your web.config file above the closing </configuration> tag:

```
<location path="DomainSynchronize.aspx">
        <system.web>
            <authorization>
                <allow users="?"/>
            </authorization>
            <httpRuntime maxRequestLength="20480" executionTimeout="600" />
        </system.web>
 </location>


```

## Troubleshooting System.OutOfMemoryException error

ASP .NET applications will throw a System.OutOfMemoryException error if they cannot allocate physical memory or reserve sufficient virtual memory to meet an allocation request. By default, the addressable virtual memory space that is available is 2 GB. If this is used, the operating system can't allocate additional memory.

This can also occur if other processes on the server are using most of the ram.

To troubleshoot the problem, follow these steps:

* Connect to the machine running your web application and open up task manager (start->run->taskmgr). Make sure other processes are not using up most of the RAM on the server. If they are, close them, migrate your application to another machine, or increase the amount of RAM available. Note that ASP .NET applications will appear as the w3wp.exe process.

* If most of the RAM is not being used, your application pool may be limited to a small amount of memory. You can increase this amount by opening the IIS manager (start->run->inetmgr), expanding the server node on the left pane, clicking on "Application Pools", right clicking on the application pool running your application, selecting "Advanced Settings", and changing the Private Memory Limit and Virtual Memory Limit in the recycling section.

## HTTP Error 404 or 404.17 - Not Found When Upgrading .NET Framework Version

### Symptom

After upgrading Password Reset Server to 4.0.000000 and changing the CLR version, when attempting to load Password Reset Server, you receive the following error in Internet Explorer:

HTTP Error 404.17 - Not Found
The requested content appears to be script and will not be served by the static file handler.

### Resolution

This error can be caused by ASP.NET 4.5 not being correctly registered on the server.

Windows Server 2012 / 2012 R2
Use the Server Manager to install ASP.NET 4.5.
1. Open the Server Manager, select "Manage" and "Add Roles and Features".
1. Select Role based or feature based installation for your server.
1. Under "Web Server (IIS)", expand "Web Server", then "Application Development".
1. Check ASP.NET 4.5.
1. Finish the wizard to complete the installation.

## TeleSign Verification

Please visit the following link for more information on [TeleSign](https://thycotic.com/products/password-reset-server/licensing/telesign-verification/).

## Proxstop Phone Verification

Please visit the following link for more information on [ProxStop](https://thycotic.com/products/password-reset-server/licensing/proxstop-phone-verification/)
