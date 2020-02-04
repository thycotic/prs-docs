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
