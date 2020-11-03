[title]: # (Configuring CEF)
[tags]: # (configuration)
[priority]: # (2)
# Configuring CEF

Password Reset Server can log to a CEF or Syslog listener. When this is configured, all important system log entries are sent to the CEF or Syslog server entered in the configuration. The written events contain data such as user information, time, IP Address, and any other important details about the event.

When in __Administration > Configuration__, click the __Edit__ button and select the __Enable Syslog/CEF Logging__ check box. When you do this, three additional settings will appear:

__Syslog/CEF Server__ 

IP address or name of the server.

__Syslog/CEF Port__

Port that the events will be sent to the server on.

__Syslog/CEF Protocol__

Either UDP or TCP, the protocol used by your server.

Once you have entered these values, click __Save__. After enabling CEF, your server should start to receive messages right away if you entered the data correctly. In order to force an event to happen, perform a log out and then log back in. If the event does not appear on your CEF server soon after, there is something wrong with your configuration.
