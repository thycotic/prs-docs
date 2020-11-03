[title]: # (Administrative Reports)
[tags]: # (report)
[priority]: # (1)
# Administrative Reports

Password Reset Server has reports available to administrators to help get a demographic for adoptions,
usages, etc. To view these reports, click the __Administration__ link on the top navigation bar and then click __Administration Reports__.
For an explanation of each report and what it represents, click __Explain__.

## Security Hardening Report

The Security Hardening Report checks aspects of Password Reset Server to ensure security best practices
are being implemented. While Password Reset Server will run with all of the items failing, administrators
should be aware of possible security issues within an installation.

Below is an explanation of the different values:

__SQL Server Authentication Password Strength__ 

SQL Server Authentication requires a Username and password. The password must be a strong password
to get a pass result. Strong passwords are 8 characters or longer and contain lowercase, uppercase,
numbers and symbols. The SQL Server Authentication Credentials in use can be changed by going to the
installer (installer.aspx) and changing them on Step 3. A pass result is also given if Windows
Authentication is used to authenticate to SQL Server. 

__SQL Server Authentication Username__ 

The SQL Server Authentication Username should not be obvious - the use of sa, prs or
passwordresetserver will give a fail result. The SQL Server Authentication Credentials in use can be
changed by going to the installer (installer.aspx) and changing them on Step 3. A pass result is also given
if Windows Authentication is used to authenticate to SQL Server. 

__Windows Authentication to Database__ 

Windows Authentication takes advantage of Windows Security to provide secure authentication to SQL
Server. The SQL Server Authentication options can be changed by going to the installer (installer.aspx)
and changing them on Step 3. Please see the [Installation Guide](../../installation/index.md) for instructions on configuring
Windows Authentication to SQL Server.

__Require SSL__ 

Secure Sockets Layer (SSL) is required to ensure that all communication between the web browser and
Password Reset Server is encrypted and secure. Once the SSL certificate is installed, Force HTTPS/SSL in
Configuration to get a pass result.

__Using SSL__ 

SSL needs to be running with at least a 128 bit key size to get a pass result. A warning result indicates
your key size is less than 128 bits. A fail result indicates you are not using SSL.

>**Note:** Use of SSL is highly recommended for Password Reset Server.