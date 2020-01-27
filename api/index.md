[title]: # (API Guide)
[tags]: # (welcome)
[priority]: # (900)

# API Guide

## Overview

Password Reset Server provides web services to allow for 3rd party developers to
interact with Password Reset Server in a developer-friendly way while
maintaining security.

The web services use a standard messaging format called Simple Object Access
Protocol (SOAP for short). SOAP is an XML based message exchange protocol to
exchange information over a standard HTTP connection.

Password Reset Server is built using version 1.2 of the SOAP protocol.

For technical details of the SOAP protocol, please refer to the W3C [here](http://www.w3.org/TR/2007/REC-soap12-part0-20070427/).

## Accessing Web Services

Password Reset Server’s web services can be accessed with the following URL:

*http://yourpasswordresetserverinstallation/webservices/webservice.asmx*

For getting the WSDL definition, append *?wsdl* to the end of the URL:

*http://yourpasswordresetserverinstallation/webservices/webservice.asmx?wsdl*