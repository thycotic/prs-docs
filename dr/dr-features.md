[title]: # (Features)
[tags]: # (disaster recovery, dr, features)
[priority]: # (701)

# Password Reset Server Disaster Recovery Features

There are many factors to a solid disaster recovery plan. Physical hardware, network connectivity, power requirements, Operating System configuration, and similar concerns are out of the scope of Password Reset Server. However, Password Reset Server can help with the management of and access to the user answers saved in the application database. It is worth noting that Password Reset Server performs well in virtual environments, integrating Password Reset Server into your virtualization solution is recommended.

## Features found in Password Reset Server

This is a complete list of Disaster Recovery Features built in to the Password Reset Server application.

- Manual Web Application Backup
- Manual Application Database Backup
- Automated Application Database Backup
- Automated Web Application Backup
- Microsoft SQL Mirroring

### Manual Web Application Backup

This is a configurable “one-click” process that creates a backup of the folder containing of the Password Reset Server application. Using this file in conjunction with a valid Password Reset Server Application Database, functionality can typically be restored in less than 30 minutes.

### Manual Application Database Backup

This is a configurable “one-click” process that creates a backup of the Password Reset Server Application Database. Restoring this database backup and reconnecting the web application to the database typically requires less than 30 minutes (depending on the size of the database being restored).

### Automated Web Application Backup

This is a scheduled version of the Manual Web Application Backup feature. This can be automated in conjunction with the backup of the Application Database.

### Automated Application Database Backup

This is a scheduled version of the Manual Application Database Backup feature. This can be automated in conjunction with the backup of the Web Application.

### Microsoft SQL Mirroring

Password Reset Server support Synchronous and Asynchronous mirroring in Microsoft SQL Server. Log File Shipping is not supported in Password Reset Server.
