[title]: # (Configuring SMTP Access)
[tags]: # (configuration)
[priority]: # (3)
# Configuring SMTP Access

Password Reset Server requires a valid SMTP server to send emails. Please contact your mail server administrator for determining your SMTP server address.

The following settings are available:

__Email Server__

The SMTP server or IP address provided by your IT administrator.

__From Email Address__

The email address that Password Reset Server will send emails from. This will appear as the “From” address when users receive emails from Password Reset Server. Depending on your email configuration, you may have to use a specific address. Contact your IT administrator for more information.

__Use SMTP Credentials__

Select this option if the SMTP Server requires specific credentials for access. When this option is selected, the domain, username, and password can be provided.

__Use SSL for SMTP__

Select this option if the SMTP Server requires access using SSL.

__Use Custom SMTP Port__

Select this option if the SMTP Server should be accessed through a non-default port (port 25 or ports 465/587 for SSL). 

To test your email configuration, click __Save__ and then click __Send Test Email__. Password Reset Server will send an email to your address using the provided configuration. You should receive an email address if the configuration setup properly.
