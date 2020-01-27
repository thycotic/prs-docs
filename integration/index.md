[title]: # (Integration)
[tags]: # (welcome)
[priority]: # (600)

# Syslog Integration Guide

## Meeting Information Security Compliance Mandates

Leveraging Password Reset Server event data with SIEM and Log Management solutions can give organizations insight into self-service reset attempts by users, and potentially malicious attacks on usernames.

**Note:** Terminology used in this document is based on the SANS Glossary of Security Terms, available at [http://www.sans.org/security-resources/glossary-of-terms/](http://www.sans.org/security-resources/glossary-of-terms/)

## Password Reset Server’s Reported Events

Table 1 is a complete list of events in Password Reset
Server’s Syslog. Both the Event Name and Event ID are contained in the log as
well as the data fields that apply to the event.

### Table 1

| Event Name | Event Id |
|---------------------------------------|--------------|
| System Log                            | 500          |
| USER - CREATE                         | 1            |
| USER - DISABLE                        | 2            |
| USER - ENABLE                         | 3            |
| USER – LOCKOUT                        | 4            |
| USER - ADDEDTOGROUP                   | 5            |
| USER - REMOVEDFROMGROUP               | 6            |
| FOLDER - CREATE                       | 7            |
| FOLDER - DELETE                       | 8            |
| ROLE - CREATE                         | 9            |
| ROLE - ASSIGNUSERORGROUP              | 10           |
| ROLE - UNASSIGNUSERORGROUP            | 11           |
| ROLEPERMISSION - ADDEDTOROLE          | 12           |
| ROLEPERMISSION - REMOVEDFROMROLE      | 13           |
| FOLDER - EDITPERMISSIONS              | 14           |
| CONFIGURATION - EDIT                  | 15           |
| USER - LOGIN                          | 16           |
| USER - LOGOUT                         | 17           |
| USER - LOGINFAILURE                   | 18           |
| USER - PASSWORDCHANGE                 | 19           |
| AD_ATTRIBUTE – ATTRIBUTE_CHANGE       | 10001        |
| AD_ATTRIBUTE – SETTING_CHANGE         | 10002        |
| REPORT - REPORT_EDIT                  | 10003        |
| REPORT - REPORT_RENAME                | 10004        |
| REPORT - REPORT_CREATE                | 10005        |
| USER - USER_IMPORTANSWER              | 10006        |
| USER - START RESET                    | 10007        |
| USER - RESET SUCCESS                  | 10008        |
| USER - RESET FAILURE                  | 10009        |
| USER - UNLOCK FAILURE                 | 10010        |
| USER - UNLOCK SUCCESS                 | 10011        |
| USER - RESET UPDATE SUCCESS           | 10012        |
| USER - RESET UPDATE FAILURE           | 10013        |
| REPORT - REPORT_DELETE                | 10014        |
| LICENSING - LICENSING INVALID         | 10015        |
| USER - HELP DESK RESET UPDATE SUCCESS | 10016        |
| USER - HELP DESK RESET UPDATE FAILURE | 10017        |

## Password Reset Data Fields

Table 2 is a complete list of data fields in Password
Reset Server’s Syslog. Only Data Fields relevant to the Event ID are included in
the log. Some log entries may differ in terms of their field content, see
examples below.

### Table 2

| Event Definition | Data Field |
|------------------------------------------|----------------|
| User ID being viewed or changed          | duid           |
| User name being viewed or updated        | duser          |
| User ID of user performing action        | suid           |
| Username of user performing action \*    | suser          |
| Description of audit action              | msg            |
| Current Version of Password Server       | Version        |
| Human readable name of event             | Name           |
| The Priority of event                    | Priority       |
| Name of company                          | Vendor         |
| Name of product                          | Product        |
| Description of audit action              | Message        |
| Time of event                            | rt             |
| IP Address of client machine             | src            |
| Name of item action was taken on         | fname          |
| Type of item action was taken on         | fileType       |
| ID of item action was taken on           | fileId         |
| Name of Role modified                    | cs1            |
| "Role"                                   | cs1label       |
| Name of User or Group added to role      | cs2            |
| "Group" or "User"                        | cs2label       |
| Name of Folder containing Secret         | cs3            |
| "Folder"                                 | cs3label       |
| Display name of user performing action \*| cs4            |
| "suser Display Name" \*                  | cs4label       |

### Example Event 1

In this event, a user has started the reset process:

```
May 15 09:39:55 THY364 CEF:0\|Thycotic Software\|Password Reset
Server\|4.1.000001\|10007\|USER - START RESET\|2\|msg=[PasswordResetServer]
Event: [User] Action: [Start Reset] By User:
test.thycotic.com\\\\THYCOTICTESTUSER Item Name:
test.thycotic.com\\\\THYCOTICTESTUSER Details THYCOTICTESTUSER suid=173
suser=test.thycotic.com\\\\THYCOTICTESTUSER cs4= duser=
test.thycotic.com\\\\THYCOTICTESTUSER duid=173 fname=
test.thycotic.com\\\\THYCOTICTESTUSER fileType=User fileId=173 src=::1 rt=May 15
2015 09:39:55
```

### Example Event 2

In this event, an administrator has edited a report.

```
May 15 09:29:12 THY364 CEF:0\|Thycotic Software\|Password Reset
Server\|4.1.000001\|10003\|REPORT - REPORT_EDIT\|2\|msg=[PasswordResetServer]
Event: [Report] Action: [Report Edit] By User: admin Details User Param suid=1
suser=admin cs4= src=::1 rt=May 15 2015 09:29:12
```