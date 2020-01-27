[title]: # (Web Service Methods)
[tags]: # (web service, methods)
[priority]: # (1)

# Web Service Methods

## Authenticate

This method is used to authenticate a username and password, and gives a token if the authentication was successful.

### Return Type

[Token](#token)

### Parameters

- domain  
    Type: string  
    Required: no  
    The domain, if attempting to authenticate using a domain account. For
    non-domain accounts, passing null, empty string, or “(local)” indicates it
    is not a domain account.

- username  
    Type: string  
    Required: yes  
    The username for authentication.

- password  
    Type: string  
    Required: yes  
    The password for authentication.

### Errors

-   “Login failed.”  
    The credentials specified are not valid, or the account is disabled, or
    locked out.

## ImportAnswer

This method is used to automatically fill out a question for a user. It allows enrollment to happen automatically.

### ReturnType

[WebServiceResult](#webserviceresult)

### Parameters

- token  
    Type: string  
    Required: Yes  
    The authentication token returned by the Authenticate method.

- domain  
    Type: string  
    Required: Yes  
    Domain of the user to enroll for this question.

- username  
    Type: string  
    Required: Yes  
    User to enroll for this question.

- questionName  
    Type: string  
    Required: Yes  
    Question to enroll the user for.

- answer  
    Type: string  
    Required: Yes  
    Answer for the question the user is being enrolled in.

- countryCode  
    Type: string  
    Required: No  
    Code for the country – used by Phone and SMS questions.

- extension  
    Type: string  
    Required: No  
    Optional extension for Phone questions.

### Errors

- “The user needs Administer Users and Bulk Import Answers permissions.”  
  The user whose token is being used for the question import does not have the Administer Users or Bulk Import Answers permissions. Assign these permissions on the Role Assignment or Role Edit pages under Administration \> Roles.

## UserEnrolled

This method is used to check whether a particular user has successfully enrolled.

### Return Type

bool

### Parameters

- domain  
    Type: string  
    Required: no  
    The domain of the user to check.

- username  
    Type: string  
    Required: yes  
    The username of the user to check the enrollment status of.
