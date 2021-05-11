[title]: # (Scenarios)
[tags]: # (disaster recovery, dr, scenarios)
[priority]: # (704)

# Scenarios

### Single Site, Single Server

Microsoft SQL Server ***Express***

Scenario 1 is an example of a standard Password Reset Server installation. Password Reset Server Standard and Microsoft SQL Server **Express** are installed on a single Windows Server (Production). A Disaster Recovery Plan for this configuration would consist of the **Manual** Web Application Backup and **Manual** Application Database Backup procedures. User-managed strategies can also be employed, such as a **Manual** File Backup and **Manual** Database Backup. If the Windows Server is virtualized, strategies such as making scheduled Snapshots or having a Hot/Cold Site would provide additional layers of redundancy. The recovery time for reverting to Password Reset Server-generated backup files is roughly 30-60 minutes plus any time needed to prepare the server for Password Reset Server installation in the user’s environment.

![Microsoft SQL Server Express](.\images\dr-1b.png)

### Single Site, Multi-Server

Microsoft SQL Server ***Standard***

Scenario 2 is an example of a common Password Reset Server installation. Password Reset Server and Microsoft SQL Server **Standard** are installed on a number of Windows Servers, with the number depending on the requirements of the organization. The diagram shows Microsoft SQL Mirroring enabled with a Witness Server, but a Witness Server is not required for this scenario. A Disaster Recovery Plan for the above configuration would consist of failover for Microsoft SQL Server issues. If the failover members were to themselves fail, then **Automated** Web Application Backups and **Automated** Application Database Backups can be used to restore functionality to the Inactive server. If these Servers are virtualized, strategies such as making scheduled Snapshots or having a Hot/Cold Site would provide additional layers of redundancy. The recovery time for reverting to Password Reset Server-generated backup files is roughly 30-60 minutes plus any time needed to prepare the server for Password Reset Server installation in the user’s environment.

![Microsoft SQL Server Standard](.\images\dr-2b.png)

### Multi-Site AlwaysOn AG - A Hot Standby Node in Another Data Center 

Microsoft SQL Server ***Standard***

Scenario 3 is an example of a Password Reset Server installation that leverages a hot standby node in another data center. In the event of a disaster, manual intervention is required to bring the web node server in that location online. Load Balancers are used to help minimize DNS-related changes during fail over events. This design variation leverages **Basic** Availability Groups as part of SQL **Standard** licensing, for a low cost, new design option to provide HA/DR for the PRS back-end database. Synchronous replication configured between data centers is advisable only when data centers are in close physical proximity to one another or latency is less than 30ms.

![Microsoft SQL Server Standard](.\images\dr-3.png)


### Multi-Site AlwaysOn AG - A Hot Standby Node in Another Data Center and a Local Hot Standby Node

Microsoft SQL Server ***Enterprise***

Scenario 4 is an example of a Password Reset Server installation that leverages multiple hot standby nodes. One is set up locally and another is set up in another data center. In the event of a disaster, manual intervention is required to bring the web node server in that location online. Load Balancers are used to help minimize DNS-related changes during fail over events. This design variation leverages **Enterprise** Availability Groups as part of SQL **Enterprise** licensing, for a low cost, new design option to provide HA/DR for the PRS back-end database. A local node is available for patching scenarios to fail the database over to another node within the same data center. Synchronous replication configured between data centers is advisable only when data centers are in close physical proximity to one another or latency is less than 30ms.

![Microsoft SQL Server Enterprise](.\images\dr-4.png)
