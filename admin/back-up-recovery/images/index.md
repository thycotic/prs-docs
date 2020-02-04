[title]: # (Backup and Disaster Recovery)
[tags]: # (recovery)
[priority]: # (1)
# Backup / Disaster Recovery

Password Reset Server supports automatic database and IIS directory backups.

From the __Backup__ page, specify the correct folder paths for the IIS Password Reset Server file directory
and the database backups to go. The backup path must be local to the server where the Password Reset Server database or file directory exists. The folders must also have the proper permissions to allow
Password Reset Server to automatically place backups in them. The account that needs permissions will be displayed as an alert on the page. There are numerous options to consider when backing up Password Reset Server. Backups can be scheduled to run on a specific time interval. To prevent the directory from growing too large, the number
of backups to keep can be defined as well. Depending on size constraints or preferences of the DBA who
would be administrating a disaster recovery scenario, the database backup can either truncate the transaction log or keep it intact.
