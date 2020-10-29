[title]: # (PRS MSI)
[tags]: # (msi)
[priority]: # (107)

# Password Reset Server MSI

Make sure you have the *prerequisites* installed before attempting to setup Password Reset Server.

## Download the latest version of Password Reset Server

The latest version of Password Reset Server is available for [download](https://thycotic.com/products/password-reset-server/resources/download/). After clicking the Download button, the setup.exe file will be downloaded to your machine.

## Running the MSI

When running the setup.exe file, your first option will be to choose Standard or Advanced.

### Standard Option

This option installs Password Reset Server as a virtual directory under the Default Website. This is recommended if you have existing sites using the Default Website, and is also the fastest way to get up and running.

### Advanced Option

This option installs Password Reset Server as a new website without using the Default Website. This allows you to specify a port number that the website will run under. Using this option assumes some knowledge of IIS and is often followed up by adding a DNS entry on the domain controller. This option must be used if there is no Default Website already present.

### File Destination

This is the location where the application files will exist. The folder is typically C:\\inetpub\\wwwroot\\PasswordResetServer but can be customized to follow your convention.

### Application Name

Application name will be used when creating the Application Pool and either the website or the virtual directory, depending on the selected option above.

### Completing Installation from Password Reset Server

Once the MSI completes, the website will be set up with the correct permissions. The browser will open to allow you to complete the Password Reset Server installation from the webpage. The following section will guide you through this process.