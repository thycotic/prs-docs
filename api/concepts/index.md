[title]: # (Concepts)
[tags]: # (concepts)
[priority]: # (1)

# Concepts

## Token

Password Reset Server requires the use of a token for most of the web service methods. A token can be acquired using the Authenticate methods.

This token is then passed to other web service methods that require it. The token contains information from when it was initially acquired, such as the date it was created for expiration purposes. Password Reset Server verifies that the token is still valid on the web service methods that use it.

The token should be persisted to storage if authentication sessions go beyond the lifetime of your application. If the token is no longer valid, you must re-authenticate to acquire a new token.

## Return Types

Password Reset Server web service methods that can fail will return a web service type that includes an Errors property, which is a collection of strings. If there is one or more string in the Errors collection, the service method is assumed to have failed. The Errors collection contains details of the nature of the failure.

For service methods that return a type without an Errors property, the service method should succeed in all cases unless otherwise noted.

## Common Errors

Web service methods, which require a token, may return the following error in addition to web service specific errors.

- "Bad token."  
    The token is no longer valid.