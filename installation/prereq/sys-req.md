[title]: # (System Requirements)
[tags]: # (requirements)
[priority]: # (102)

# System Requirements

## Software Requirements

- One of the following operating systems:

    - Windows 8 or 8.1 <sup>**1**</sup>

    - Window Server 2012 or 2012 R2 <sup>**2**</sup> 

        

- Microsoft SQL Server 2005, 2008 or 2012, including R2 (any edition)

- Microsoft **Internet Information Services** (IIS) (internal part of the operating system)

- **Microsoft .NET Framework 4.5.1 / 4.5.2** (both 32-bit and 64-bit editions are supported)

**Note:** Windows 8 / 8.1 and Windows Server 2012 / R2 come with the .NET Framework 4.5.1 already installed. If you are using Windows 8 or Windows Server 2012, you should already have .NET Framework 4.5 but will need to upgrade to .NET Framework 4.5.1 / 4.5.2. Find the installer provided by Microsoft [here](http://www.microsoft.com/en-us/download/details.aspx?id=40779).

## Domain Account Requirements

Each domain will need a domain account to synchronize the users and reset passwords. See the [Appendix](..\appendix\index.md) for instructions to set up the domain account.

## Additional Recommendations

- Use an [SSL certificate](..\appendix\index.md#sslcertificate) for Password Reset Server.

- Run [Microsoft Update](http://update.microsoft.com/) on your server to make sure all components are up to date.

<sup>**1**</sup> Windows 8 and 8.1 are only supported for testing environments. Microsoft does not support either of these operating systems being used as a production server environment.

<sup>**2**</sup> Both 32-bit and 64-bit editions of Windows Server are supported. You must install the proper version of the .NET Framework to support 64-bit.