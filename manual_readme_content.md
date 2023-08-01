
Shodan collects data mostly on web servers (HTTP, port 80), as well as FTP (port 21), SSH (port 22)
Telnet (port 23), SNMP (port 161), SIP (port 5060),\[2\] and Real Time Streaming Protocol (RTSP,
port 554).

### Suggested Use-cases

This app can be used to check whether or not a given IP address is listening given ports. This
allows us to gain information that is: credible, publicly accessible, and does not require a single
packet to be sent to the target IP address.

For Example:

-   For alerts about an inbound connection, phantom can validate whether or not the service is
    publicly accessible.
-   For alerts regarding outbound connections (irc, smtp, ntp, etc.) this can be used to verify
    whether or not the host is hosting that service and what service is listening on that port.
-   Perform reconnaissance on internet hosts

### Future Features

Currently, this app performs a lookup against a domain or ip address for open ports and services.

Future areas of expansion include:

-   Implement more specific checks to look for specific IP *and* Port
-   Implement checks to support IP ranges / CIDR blocks
-   Triggering on-demand scan for paid developer accounts
-   DNS forward and reverse resolution
-   Implement widgets (Webpage Thumbnails, etc.)

### Requirement

In order to use this app, you must obtain an API key from Shodan.io. A free API key can be obtained
from the Shodan.io website by registering and visiting your [account
page](https://account.shodan.io)

### References

-   Shodan Developer Reference: <https://developer.shodan.io/api>
-   Shodan Search Page: <https://www.shodan.io>
