[title]: # (PRS MSI)
[tags]: # (msi)
[priority]: # (107)

# Password Reset Server MSI

Make sure you have the *prerequisites* installed before attempting to setup Password Reset Server.

## Download the latest version of Password Reset Server

To download the installation file for the newest version of Password Reset Server, go to our [Support Community](https://thycotic.force.com/support/s/) page, log in, and click the Password Reset Server panel. Follow the prompts to navigate to the new download page, where you can download the **Installer (.msi)** file for automated installation.

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