[title]: # (General Configuration)
[tags]: # (configuration)
[priority]: # (1)
# General Configuration

Password Reset Server’s configuration can be accessed by logging in as an administrator, clicking __Administration__ in the top navigation bar, then selecting __Configuration__.

The following settings are available:

__Allow Automatic Update Checks__

When automatic update checks is on, Password Reset Server will perform background checks to see if there are any updates available for download. If updates are available, there will be a notice and link at the top of the page to download the updates. When automatic updates is off, the background check is not done and no notice about updates will be shown on the page. 

__Default Theme__

Password Reset Server ships with two themes, a default theme, and a red theme. The theme setting will apply to all users.

__Default Date Format__

The default date format controls how dates are formatted in Password Reset Server.

__Windows Client Language__

This setting determines the language which is displayed when using the Windows logon integration client.

__Force HTTP/SSL__

When this setting is on, requests coming in to Password Reset Server using HTTP will be redirected to use HTTPS.

__Enable Email Sign In__

When this setting is on, users will be able to log into Password Reset Server using their email addresses instead of their Active Directory usernames.

__Enable Domain Selector Login__

This setting determines what users see when they login or try to do a password reset.

* __Show Domain Drop Down:__ Users see a drop down with all domains listed. This is the default behavior.
* __Show Domain Label:__ Users see a label with the default domain.
* __Hide Domain Info:__ Completely hides all domain info.

If the domain drop down is not used, the domain used will be the user’s last used domain. If they are logging in for the first time it will be the default domain as specified under __Administration | Domain Configuration__. Users can specify a different domain than the default by using their UPN, email, or by specifying their username as DOMAIN\Username. To login as the local admin, use LOCAL\username or .\username.

__URL for User Help Link__

Set a custom help link in the Password Reset Server footer for end users to take them to an internal custom page describing your organization’s password reset policies and procedures.

__Email for User Error Submission__

Set a custom email address for users to submit any exceptions they run into. This should be the IT owners of Password Reset Server so end user issues can be addressed.
