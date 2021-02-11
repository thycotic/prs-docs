[title]: # (Maintaining PRS in a Disaster)
[tags]: # (disaster recovery, dr, maintenance)
[priority]: # (702)

# Maintaining Password Reset Server in a Disaster

The framework of a solid Password Reset Server Disaster Recovery Plan should follow these methods of maintaining operations. Thycotic Software recommends geographic redundancy when and where economically feasible. Multiple sites are not required by any means, but work to ensure network, power and hardware replication between Password Reset Server instances.

## Simple Installation & Architecture

Password Reset Server can operate on typical modern servers and even workstations in the simple configurations without requiring high-end hardware.

[Password Reset Server System Requirements](https://updates.thycotic.net/link.ashx?PRSSystemReqs)

By design, Password Reset Server’s installation is a quick and easy process. Keeping the installation process quick and easy was a goal from the very first release of Password Reset Server (as a security product it should be very easy to upgrade should security fixes need to be applied). This serves as a viable fallback option should redundancy plans fail. In a worst-case scenario where the host server fails, a mirror fails, and the other backup plans fail, Password Reset Server can be installed from scratch quickly and data imported from various methods. Users familiar with Microsoft SQL and IIS can typically install Password Reset Server in about 30-45 minutes on a prepared server.

Review the installation guides on our [Support page](https://thycotic.com/support/password-reset-server/).

## Automated & Manual Backups

Password Reset Server natively supports local and network backups. By configuring locations for the application folder and Microsoft SQL database, Password Reset Server backs up this data based on a highly-configurable user-defined schedule with detailed logging. Please refer to the following documentation for Automated Backup configuration:

[Backing up to a Network Share](https://updates.thycotic.net/link.ashx?BackupToNetworkShare)

[Backup Configuration File Path Settings](https://updates.thycotic.net/link.ashx?BackupDatabaseFilePath)

[Manual Backup Procedures](https://docs.thycotic.com/prs/5.2.0/admin/back-up-recovery/index.md)


## Restoring from Backup

Restoring Password Reset Server’s web application folder is as simple as copying the contents of the last available zipped backup file back into folder. Microsoft SQL database restores are simple as well but require several steps depending on the backup scenario.

## Microsoft SQL Server Mirroring & High Availability

Password Reset Server supports Synchronous/Asynchronous Microsoft SQL Mirroring. Mirroring database instances is an important part of any high-availability Business Continuity Plan. Adding geographic redundancy to this plan is recommended for customers with multiple sites, for that added layer of protection. To use a mirrored database with Password Reset Server, ensure that the Failover Partner is set in the database configuration installation step.

See the Microsoft documentation [here](https://docs.microsoft.com/en-us/sql/?view=sql-server-ver15).
