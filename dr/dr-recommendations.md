[title]: # (Recommendations)
[tags]: # (disaster recovery, dr, recommendations)
[priority]: # (703)

# Disaster Recovery Recommendations

When using a configuration without multiple servers, making frequent backups is the best solution. However, using a virtual server is the preferable choice when using the single server approach. Virtual servers allow the System Administrator to make a full backup of the server in addition to backups within Password Reset Server. They also allow for the server to be transferred to different hardware quickly. Regardless of using a physical server or virtual server, suggestions for Disaster Recovery Plans are listed below.

## Backups

Make frequent (at least daily) backups. Password Reset Server supports creating backups manually and on a schedule. To make a backup within Password Reset Server, login in as an Administrator. Then, click on Administration \> Backup. Choose a location for the backup.

**Note:** In single server configurations, it is highly recommended to save the backup files for Password Reset Server on a different device. This will isolate sensitive files from a hardware failure on that server.

## Restore

When restoring from backup in the single-server configurations, be certain to make copies of the Password Reset Server backup files on a different device or media.

Start by preparing a server for installation as the Installation Guide instructs. When the server is prepared, restore the application and database. This guide below will explain the procedure of restoring the database. Some specific web configurations may be needed to match the previous IIS settings. If you are unable to restore Password Reset Server after following these steps, please contact [Technical Support](https://updates.thycotic.net/link.ashx?TechSupport). It is recommended to configure a second server or Virtual Machine after setting up the primary server. Then the process of restoring from the Password Reset Server backups is simply a matter of copying the files to the pre-configured server and restoring them.

Moving the location of the database to a different server adds an additional layer of reliability.

## Redundant Servers

Password Reset Server supports several features that allow the uninterrupted operation of the application. Using Microsoft SQL Mirroring, the Password Reset Server Application Database can be automatically replicated to a second database server. Make use of multiple servers when logistically and economically feasible.

Use mirroring if at all possible. Mirrored databases are a reliable method of maintaining operations when servers fail. Password Reset Server supports both Asynchronous and Synchronous Mirroring. However, Log File Shipping is not supported. To enable Microsoft SQL Mirroring in Password Reset Server, use the following article:

[Microsoft SQL Server Mirroring](https://updates.thycotic.net/link.ashx?SQLServerMirroring)

The Web Application does not support clustered installations at this time. The recommended configuration is to configure a secondary web server and copy over a production backup of the Password Reset Server application folder and configure the site. Once it is pointed at the mirror, the site can be switched off in IIS. If the primary web server goes down, then an application backup can be restored onto the pre-configured server and the site enabled. Since it would be pointing to a mirror, there would be no need to restore a database backup in this scenario thus reducing downtime.