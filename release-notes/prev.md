[title]: # (5.1.000006 and Previous Release Notes)
[tags]: # (release notes)
[priority]: # (1002)
# Password Reset Server Release Notes for 5.1.000006 and Previous 

## Password Reset Server Version 5.1.000006 (Fall Maintenance Release)

### Upgrade Notes

Password Reset Server Version 5.1.000006
September 9, 2020

__Security:__

* Fixed a vulnerability in GINA client which could lead to remote code execution and was only present if the attacker had control over network communications.
* Fixed a vulnerability in GINA client which could lead to remote code execution. Security Issue Discovered by:
   * __Barrett Adams__ (Lead Researcher) of Specter Ops and __Rick Romo__, __Angel Flores__, and __Marcus Sailler__ of Capital Group Companies.

__September 24, 2019__ 

To take advantage of updates to the Windows logon integration (WLI) desktop application in this release, you will need to uninstall and re-install your WLI files after upgrading PRS. Before doing so, perform the workaround steps listed below.

__Known Issue__: After installing Windows logon integration, customers may see the message "This machine is not registered for offline reset" on the Windows logon screen even though they have enabled offline reset.

__Workaround__: Before installing or re-installing Windows logon integration, the installer files may need updating by making a change in the configuration:

   >**Note;** Administrator permissions are necessary to make these changes.

1. Go to CreateConfigurationFiles.aspx.
1. Click the __Edit__ button.
1. Do not change anything
1. Click the __Save__ button.
1. Download and reinstall Windows login integration.

### Enhancements and Security

__Updated JQuery Libraries__

Updated JQuery libraries to JQuery version 3.4.1., eliminating an XSS vulnerability.

__SQL Security Vulnerability__ 

Fixed a SQL injection security vulnerability

__Support for Special Characters Used in XML__

Updated the PRS configuration setting “App Host URL” and all Windows-logon-integration localized text settings to support XML special characters and address an XML vulnerability.

__Modern SSL Protocols__

Updated Windows logon integration desktop application to allow communications over modern SSL protocols, including TLS 1.1 and TLS 1.2. This addressed a reported issue where PRS attempted to make calls over HTTP instead of HTTPS. This issue could occur when PRS and the machine hosting the Windows logon integration fail to find a common secure protocol. In addition:

   * All customers should verify that the PRS certificate is valid and works in Internet Explorer because the issue may be environmental.
   * Windows 7 customers (and those using .NET 2.0) should verify that registry settings to support TLS 1.1 and TLS 1.2 are in place on the local machine.

### General

__No Longer Force Users to Reset Their Password After Reset__

Added a new “ResetWithoutChangeOnNextLogon” application setting that allows administrators to change the default Password Reset Server (PRS) behavior where users are prompted to change passwords at next logon immediately after performing an offline password reset.

Typically, when a user performs a password reset through PRS, it sets an attribute in Active Directory that forces them to change their password on their next logon. After setting the new “ResetWithoutChangeOnNextLogon” setting to “True,” PRS users can use the newly set password until the normally configured expiration time. To set this new app setting to True, follow these steps:

   >**Note:** Administrator permissions are necessary to change app settings.

1. Open Windows File Explorer or another file manager.
1. Navigate to your PRS installation directory, which is usually `C:\inetpub\wwwroot\PasswordResetServer\`.
1. Right click the web-appSettings.config file, and select Open With, and select Notepad or other text editor. The XML file opens.
1. Type the following text inside the `<appSettings>` brackets:
   `<add key="ResetWithoutChangeOnNextLogon" value="True" />`
1. Save the file.
1. Restart IIS on the server.

__Do Not Differentiate “Too Many Attempts” Login Errors__ 

Updated PRS behavior to allow masking logon error differences between valid and invalid usernames during failed logons. The default behavior in PRS provides users with a new “Login Failed” message after hitting the maximum number of logon attempts for their username.

The regular logon failure message states:

__Login Failed__

The “too many attempts” message states:

“You have reached the maximum number of login attempts. Please try again later. If you have forgotten your password, please utilize the “Reset My Password” function below."

This can be undesirable because it implies that the username the user entered is in fact a valid username because PRS had to associate a username with the logon to count the attempts.

If you want to avoid this and display the same message for all users, regardless of reaching the maximum logon attempts, we now provide a “MaximumLoginAttemptsHaveBeenReachedJustLockedOut” setting to allow for customizing the “maximum attempts” error message, so you can now set it to the exact same message as the regular logon error message, eliminating the username inference.

To configure this behavior, follow these steps:

   >**Note:** Administrator permissions are necessary to make these changes.

1. Open Windows File Explorer or another file manager.
1. Navigate to the ninth PRS resource directory, which is usually `C:\inetpub\wwwroot\PasswordResetServer\resources\9`.

   >**Note:** he number representing the final subdirectory can vary, depending on the languages you set up.

1. Right click the pages.xml file, and select Open With, and select Notepad or other text editor. The XML file opens.

1. Ensure the LoginFailed, MaximumLoginAttemptsHaveBeenReachedJustLockedOut, and MaximumLoginAttemptsHaveBeenReachedsettings are all set to “Login Failed,” or any consistent message according to your company’s preference.
1. Save the file.
1. Restart IIS on the server.

### Bug Fixes

__Custom Images__

Fixed an issue where custom images were not properly loading in PRS and in emails.

Customer-provided images were not loading in e-mail templates because they did not contain a valid organization ID. Now the organization ID defaults to 1 for every image uploaded, since multiple-organizations are not supported in PRS.

Also enhanced logging and logic flow so it will report which images failed to load and if a substitute image was used in the case of a company logo.

__Active Directory Passwords__ 

Fixed a bug where Active Directory (AD) users with expired passwords attempted to logon to PRS received an “Access Denied” message and their AD passwords would automatically set to “Never Expire.”

To resolve this issue, code was removed that set the user’s PwdLastSetAttribute in AD to a value other than 1 or 0. Only Windows itself can change PwdLastSet to a value other than 1 or 0.

__Grayed Out Reset Button Issues__ 

Fixed a bug during the password reset process where the “Reset” button remained grayed out on the page but was still active. Clicking the button changed the user’s password, and clicking anywhere else on the page activated the button.

   >**Note:** This issue was resolved for users accessing PRS through supported Web browsers, but when accessing PRS through the Windows logon integration desktop application, users must still click anywhere on the page before the “Reset” button looks activated.

__Windows Logon Integration Desktop Application Offline Reset__

Fixed an issue in the Windows logon integration desktop application where offline reset remained enabled, even after re-installing the application.

The issue occurred because the offline reset is enabled via registry keys. Previously those keys were added with every install. Now, before the keys are added, there is a check to make sure if offline reset is enabled. If it is not, the keys are not added. Also, the registry values are now removed upon uninstall.

__Erroneous Error Message for Failed PRS Agent Connection__ 

Updated error messaging to be “Offline Reset Agent Configuration Issue” when PRS agents are unable to connect with the server. This error previously displayed “Offline Reset Disabled,” which was misleading.

__New Error Messages for Offline Reset__

Added error messaging for when the Windows logon Integration desktop application fails to receive information from the PRS server regarding whether the registry keys need to enable offline reset or not.

We added a third offline reset localization string to the PRS Web client called “Offline Reset Setup Failure.” It contains text explaining a setup error occurred and instructs users they should verify the application host URL is reachable and then re-install the PRS logon client. Offline Reset installation states now include: Enabled, Disabled, and Setup Failure.

__Custom Port Connections to Windows Logon Integration__

Updated the Windows logon integration desktop application to respect a custom port when entered as part of the host on the Application URL Configuration page. This update only applies to HTTPS connections