[title]: # (Password Reset Server)
[tags]: # (welcome)
[priority]: # (1)
# Password Reset Server

This is the installation guide for Windows 8 and Windows Server 2012, as well as
Windows 8.1 and Windows Server 2012 R2. If you are looking for the installation
guide for Windows Server 2008 / 2008 R2, Vista, or Windows 7, please [click
here](https://updates.thycotic.net/link.ashx?PRSSupport).

## ASP.NET Website

Password Reset Server is installed as an ASP.NET website. The MSI will setup the
website with the correct permissions and configure the appropriate settings in
IIS. Once the website is set up, the installation will be completed by a process
within the application itself.

## SQL Server Database

Password Reset Server requires an instance of SQL Server for the database
backend. The SQL Server database will require a SQL account with db_owner
permission to complete the installation.

## Administrative Access

Throughout the installation, you will be required to be an administrator to
perform most of these actions. Please ensure that you are logged on to your
system with a Windows account that has administrative permissions.
