[title]: # (Prerequisites)
[tags]: # (prerequisites)
[priority]: # (101)

# Prerequisites

Minimum requirements for installing Password Reset Server

## Hardware Requirements
 
* **CPU**: Minimum of 2 cores, 2 Ghz or higher per core 

* **RAM/Memory**: Minimum 4GB

* **Disk Space**: Minimum 20GB (mainly for the database, operating system, other applications/tools)

_**Please Note**: Hardware requirements depend on the target system and projected usage volume, and they are subject to change._

## Software Requirements

_**Please Note**:_ 
 * _DO NOT install Password Reset Server on a domain controller, because Microsoft [ASP.NET](https://dotnet.microsoft.com/apps/aspnet "ASP.NET") will not operate reliably._

* _We do not recommend installing Password Reset Server as a Web Server on a client operating system for production use (testing purposes or proof of concept only). This includes all standard Windows operating systems (Vista 10 and later)._

### Microsoft Windows Server
* 2008 
* 2008 R2
* 2012
* 2016

_**Please Note**:_
* _Small Business Server (SBS) is not supported._

* _The Essentials edition is not supported because it requires the domain controller role._

* _The “Core” (GUI-less) role is only supported for Server 2012 and Server 2012 R2._

### Microsoft SQL Server
* 2005
* 2008
* 2008 R2
* 2012
* 2014
* 2016

_**Please Note**: Edition must be SQL Server Express or higher._

### Microsoft Internet Information Services (IIS)
* IIS 7
* IIS 8

_**Please note**: You must add IIS as a feature in Windows Server. See the information [here](hhttps://docs.microsoft.com/en-us/previous-versions/orphan-topics/ws.11/hh831475(v=ws.11)?redirectedfrom=MSDN "Install IIS")_.

### Microsoft .NET Framework
* .NET 4.5.1
* .NET 4.5.2
 
## Database Size Recommendations

* 1 GB initial database size minimum.
* Typical database size for 1000 users is around 300 MB.
* Growth depends on the size of the domain (OUs, groups, users) and audit activity.

## Important Notes

* Password Reset Server will operate in a virtual environment (VMware or Hyper-V).  
* Windows Login Integration (GINA Hook) is compatible on Windows XP through Windows 10.
* You can run Password Reset Server on the same machine as other applications (Password Reset Server will require sufficient RAM and CPU to operate normally).
* For maximum security, you should install the application on dedicated systems or at least systems with applications with the same level of security/sensitivity.  Access to these systems should then be restricted.  While all sensitive data in Password Reset Server is either securely hashed or encrypted, it is a security best practice to limit any opportunities for foul play.
* Password Reset Server 3.3.000000 and higher requires the .NET Framework 4.5.1 to be installed on the web server prior to installation or upgrade. 
