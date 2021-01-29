[title]: # (Adding Custom Attributes)
[tags]: # (attributes)
[priority]: # (3)
# Adding Custom Attributes

For environments that include additional or custom Active Directory attributes, Password Reset Server
supports defining custom attributes to be synchronized. To add a custom attribute, select __Active
Directory Attributes__ from the __Administration__ menu and then select the attribute type in the drop-down
menu in the last row of the __Type__ column. There are three options:

__Text__ 

An attribute that contains a text-based value. This type of attribute will be made available as an answer
for any text-based question.

__Phone__ 

An attribute that will be formatted as a phone number. Phone type attributes are made available as
answers for multifactor Phone and SMS questions.

__Email__ 

An attribute that will be formatted as an email address. Email type attributes are made available as answers for multifactor Email questions. In the __Display Name__ field, fill in the name that you would like to reference the attribute by in Password
Reset Server when configuring the attribute as an answer source. The __AD Attribute__ column must include the name by which the attribute is referenced in Active Directory.

__Client Password Validation__ 

For Password Reset Server users, password requirements are typically managed by Active Directory Group Policy. If the password the user enters does not comply with the AD Group Policy, the user receives a general error and the reset request is not sent. Custom Client Password Validation allows administrators to set password requirements beyond what AD Group Policy can enforce.

*Implementation*

Custom Password Validation is implemented using an app setting, so you must log into the IIS host server and navigate to the installation directory, which is typically **C:\inetpub\wwwroot\PasswordResetServer**. Open the file named **web-appSettings.config** to add the **ClientPasswordValidation** key with regex statements like those below:
~~~~
<?xml version="1.0" encoding="utf-8" ?>
  <appSettings>
     <add key="ChartImageHandler" value="Storage=memory;Timeout=10;Url=~/tempimages/;"/>
     <add key="ShouldValidateResetCredentials" value="True"/>
     <add key="IsDebugLoggingEnabled" value="False"/>
     <add key="UserErrorPage" value="~/CustomError.aspx"/>
     <add key="ClientPasswordValidation" value="{
        &quot;Please use at least one digit&quot; : &quot;\\d&quot;,
        &quot;Please use at least one letter&quot; : &quot;[a-zA-Z]&quot;,
        &quot;Please use at least one symbol&quot; : &quot;[!@#$%^&*]&quot;,  
        &quot;Please use at least ten characters&quot; :  &quot;(\\w){10,}&quot;,   
        &quot;Please use no repeating characters&quot; : &quot;^(?!.*(\\w).*\\1).+$&quot;}"  

/>
~~~~