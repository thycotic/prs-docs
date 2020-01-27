Overview
========

Password Reset Server provides web services to allow for 3rd party developers to
interact with Password Reset Server in a developer-friendly way while
maintaining security.

The web services use a standard messaging format called Simple Object Access
Protocol (SOAP for short). SOAP is an XML based message exchange protocol to
exchange information over a standard HTTP connection.

Password Reset Server is built using version 1.2 of the SOAP protocol.

For technical details of the SOAP protocol, please refer to the W3C here:

<http://www.w3.org/TR/2007/REC-soap12-part0-20070427/>

Accessing Web Services
======================

Password Reset Server’s web services can be accessed with the following URL:

*http://yourpasswordresetserverinstallation/webservices/webservice.asmx*

For getting the WSDL definition, append *?wsdl* to the end of the URL:

*http://yourpasswordresetserverinstallation/webservices/webservice.asmx?wsdl*

Concepts
========

Token
-----

Password Reset Server requires the use of a token for most of the web service
methods. A token can be acquired using the Authenticate methods.

This token is then passed to other web service methods that require it. The
token contains information from when it was initially acquired, such as the date
it was created for expiration purposes. Password Reset Server verifies that the
token is still valid on the web service methods that use it.

The token should be persisted to storage if authentication sessions go beyond
the lifetime of your application. If the token is no longer valid, you must
re-authenticate to acquire a new token.

Return Types
------------

Password Reset Server web service methods that can fail will return a web
service type that includes an Errors property, which is a collection of strings.
If there is one or more string in the Errors collection, the service method is
assumed to have failed. The Errors collection contains details of the nature of
the failure.

For service methods that return a type without an Errors property, the service
method should succeed in all cases unless otherwise noted.

Common Errors
-------------

Web service methods, which require a token, may return the following error in
addition to web service specific errors.

-   "Bad token."  
    The token is no longer valid.

Web Service Methods
===================

### Authenticate

This method is used to authenticate a username and password, and gives a token
if the authentication was successful.

#### Return Type

[Token](#token)

#### Parameters

-   domain  
    Type: string  
    Required: no  
    The domain, if attempting to authenticate using a domain account. For
    non-domain accounts, passing null, empty string, or “(local)” indicates it
    is not a domain account.

-   username  
    Type: string  
    Required: yes  
    The username for authentication.

-   password  
    Type: string  
    Required: yes  
    The password for authentication.

#### Errors

-   “Login failed.”  
    The credentials specified are not valid, or the account is disabled, or
    locked out.

### ImportAnswer

This method is used to automatically fill out a question for a user. It allows
enrollment to happen automatically.

#### ReturnType

[WebServiceResult](#webserviceresult)

#### Parameters

-   token

>   Type: string

>   Required: Yes

>   The authentication token returned by the Authenticate method.

-   domain

>   Type: string

>   Required: Yes

>   Domain of the user to enroll for this question.

-   username

>   Type: string

>   Required: Yes

>   User to enroll for this question.

-   questionName

>   Type: string

>   Required: Yes

>   Question to enroll the user for.

-   answer

>   Type: string

>   Required: Yes

>   Answer for the question the user is being enrolled in.

-   countryCode

>   Type: string

>   Required: No

>   Code for the country – used by Phone and SMS questions.

-   extension

>   Type: string

>   Required: No

>   Optional extension for Phone questions.

#### Errors

-   “The user needs Administer Users and Bulk Import Answers permissions.”

>   The user whose token is being used for the question import does not have the
>   Administer Users or Bulk Import Answers permissions. Assign these
>   permissions on the Role Assignment or Role Edit pages under Administration
>   \> Roles.

### UserEnrolled

This method is used to check whether a particular user has successfully
enrolled.

#### Return Type

bool

#### Parameters

-   domain  
    Type: string  
    Required: no  
    The domain of the user to check.

-   username  
    Type: string  
    Required: yes  
    The username of the user to check the enrollment status of.

Web Service Types
=================

### WebServiceResult

WebServiceResult is a generic result that does not return any information except
Errors.

#### Members

-   Errors  
    Type: string array  
    SOAP Type: ArrayOfString. A complex type of a sequence of strings with an
    unbounded number of occurrences.  
    One or more errors that occurred during the operation.
