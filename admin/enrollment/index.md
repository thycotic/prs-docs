[title]: # (Enrollment)
[tags]: # (enrollment)
[priority]: # (1)
# Enrollment

Before a user can use Password Reset Server to reset their password, they must complete the enrollment
process. A user logging into Password Reset Server whose Active Directory account has been marked
“User must change password at next logon” will be taken to the __Change Password__ page before they are
able to enroll.

>**Note**: If the user was added to Active Directory, but Password Reset Server has not yet synced with Active Directory, Password Reset Server will initiate a sync to attempt to find the new user when they
attempt to enroll. This setting can be disabled, if desired, via the __Synchronize on New User Login__ setting on the __Domain Configuration__ page.