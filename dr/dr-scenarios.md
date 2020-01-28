[title]: # (Disaster Recovery Scenarios)
[tags]: # (disaster recovery, dr, scenarios)
[priority]: # (704)

# Scenarios

## Single Site, Single Server

*Microsoft SQL Server Express*

![Microsoft SQL Server Express](.\images\dr-1.png)

Scenario 1 is an example of a standard Password Reset Server installation. Password Reset Server Standard and Microsoft SQL Server are installed on a single Windows Server (Production). A Disaster Recovery Plan for this configuration would consist of the Manual Web Application Backup and Manual Application Database Backup procedures. In addition, user-managed strategies can be employed such as a Manual File Backup and Manual Database Backup. If the Windows Server is virtualized, leveraging strategies such as making scheduled Snapshots or having a Hot/Cold Site would add additional layers of redundancy. The recovery time for reverting to Password Reset Server-generated backup files is roughly 30-60 minutes plus any time needed to prepare the server for Password Reset Server installation in the user’s environment.

## Single Site, Multi-Server

*Microsoft SQL Server Standard*

![Microsoft SQL Server Standard](.\images\dr-2.png)

Scenario 2 is an example of a common Password Reset Server installation. Password Reset Server and Microsoft SQL Server Standard are installed on a varied number of Windows Servers. The number of servers present depends on the requirements of the organization. The above example shows Microsoft SQL Mirroring enabled with a Witness Server. However, a Witness Server is not required. A Disaster Recovery Plan for the above configuration would consist of failover for Microsoft SQL Server issues. If the failover members were to themselves fail, then Automated Web Application Backups and Automated Application Database Backups can be used to restore functionality to the Inactive server. If these Servers are virtualized, leveraging strategies such as making scheduled Snapshots or having a Hot/Cold Site would add additional layers of redundancy. The recovery time for reverting to Password Reset Server-generated backup files is roughly 30-60 minutes plus any time needed to prepare the server for Password Reset Server installation in the user’s environment.