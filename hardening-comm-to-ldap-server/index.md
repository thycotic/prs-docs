[title]: # (Hardening PRS Communication to the LDAP Server)
[tags]: # (hardening,security,ldap)
[priority]: # (1050)

# Best Practices for Hardening PRS Communication to the LDAP Server

To prevent opening a security vulnerability for Password Reset Server, especially when PRS is installed in the DMZ or is exposed to the public internet, outgoing requests over ports 389 and 636 should be blocked by an outbound firewall rule, except those intended for the legitimate LDAP server.  

On the Password Reset Server host, this configuration can be accomplished by creating two custom outbound rules in a specific order. You must create and execute the **Allow** rule first, and then create and execute the **Block** rule.

1. **Allow**. First, create an outbound rule to allow PRS to connect to your internal LDAP server over LDAP ports 389 and 636 only.

1. **Block**. Then, create a second outbound rule to block PRS from connecting to other LDAP servers/endpoints on LDAP ports 389 and 636.
