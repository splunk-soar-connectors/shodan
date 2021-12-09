[comment]: # "Auto-generated SOAR connector documentation"
# Shodan

Publisher: Ryan Kranz  
Connector Version: 1\.0\.6  
Product Vendor: Shodan  
Product Name: Shodan  
Product Version Supported (regex): "\.\*"  
Minimum Product Version: 1\.0\.240  

This app implements investigative actions like <b>query ip</b> and <b>query domain</b> to get information from the shodan search engine\.


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


### Configuration Variables
The below configuration variables are required for this Connector to operate.  These variables are specified when configuring a Shodan asset in SOAR.

VARIABLE | REQUIRED | TYPE | DESCRIPTION
-------- | -------- | ---- | -----------
**api\_key** |  required  | string | Shodan API Key

### Supported Actions  
[test connectivity](#action-test-connectivity) - Validate the asset configuration for connectivity\.  
[query ip](#action-query-ip) - Search Shodan\.io for discovered service info  
[query domain](#action-query-domain) - Search Shodan\.io for discovered service info  

## action: 'test connectivity'
Validate the asset configuration for connectivity\.

Type: **test**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
No Output  

## action: 'query ip'
Search Shodan\.io for discovered service info

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**ip** |  required  | IP to query | string |  `ip` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.ip | string |  `ip` 
action\_result\.data\.\*\.os | string | 
action\_result\.data\.\*\.opts | string | 
action\_result\.data\.\*\.domains\.\*\. | string | 
action\_result\.data\.\*\.deprecated\.html\.eol | string | 
action\_result\.data\.\*\.deprecated\.html\.new | string | 
action\_result\.data\.\*\.deprecated\.title\.eol | string | 
action\_result\.data\.\*\.deprecated\.title\.new | string | 
action\_result\.data\.\*\.deprecated\.opts\.pem\.eol | string | 
action\_result\.data\.\*\.deprecated\.opts\.pem\.new | string | 
action\_result\.data\.\*\.deprecated\.opts\.robots\.eol | string | 
action\_result\.data\.\*\.deprecated\.opts\.robots\.new | string | 
action\_result\.data\.\*\.deprecated\.opts\.sitemap\.eol | string | 
action\_result\.data\.\*\.deprecated\.opts\.sitemap\.new | string | 
action\_result\.data\.\*\.html | string | 
action\_result\.data\.\*\.http\.host | string | 
action\_result\.data\.\*\.http\.html | string | 
action\_result\.data\.\*\.http\.title | string | 
action\_result\.data\.\*\.http\.robots | string | 
action\_result\.data\.\*\.http\.server | string | 
action\_result\.data\.\*\.http\.location | string | 
action\_result\.data\.\*\.http\.html\_hash | numeric | 
action\_result\.data\.\*\.http\.redirects\.\*\.data | string | 
action\_result\.data\.\*\.http\.redirects\.\*\.host | string | 
action\_result\.data\.\*\.http\.redirects\.\*\.location | string | 
action\_result\.data\.\*\.ssl\.cert\.issued | string | 
action\_result\.data\.\*\.ssl\.cert\.issuer\.C | string | 
action\_result\.data\.\*\.ssl\.cert\.issuer\.O | string | 
action\_result\.data\.\*\.ssl\.cert\.issuer\.CN | string | 
action\_result\.data\.\*\.ssl\.cert\.issuer\.OU | string | 
action\_result\.data\.\*\.ssl\.cert\.pubkey\.bits | numeric | 
action\_result\.data\.\*\.ssl\.cert\.pubkey\.type | string | 
action\_result\.data\.\*\.ssl\.cert\.serial | numeric | 
action\_result\.data\.\*\.ssl\.cert\.expired | boolean | 
action\_result\.data\.\*\.ssl\.cert\.expires | string | 
action\_result\.data\.\*\.ssl\.cert\.sig\_alg | string | 
action\_result\.data\.\*\.ssl\.cert\.subject\.C | string | 
action\_result\.data\.\*\.ssl\.cert\.subject\.L | string | 
action\_result\.data\.\*\.ssl\.cert\.subject\.O | string | 
action\_result\.data\.\*\.ssl\.cert\.subject\.CN | string | 
action\_result\.data\.\*\.ssl\.cert\.subject\.OU | string | 
action\_result\.data\.\*\.ssl\.cert\.subject\.ST | string | 
action\_result\.data\.\*\.ssl\.cert\.version | numeric | 
action\_result\.data\.\*\.ssl\.cert\.extensions\.\*\.data | string | 
action\_result\.data\.\*\.ssl\.cert\.extensions\.\*\.name | string | 
action\_result\.data\.\*\.ssl\.cert\.extensions\.\*\.critical | boolean | 
action\_result\.data\.\*\.ssl\.cert\.fingerprint\.sha1 | string | 
action\_result\.data\.\*\.ssl\.cert\.fingerprint\.sha256 | string | 
action\_result\.data\.\*\.ssl\.chain\.\*\. | string | 
action\_result\.data\.\*\.ssl\.cipher\.bits | numeric | 
action\_result\.data\.\*\.ssl\.cipher\.name | string | 
action\_result\.data\.\*\.ssl\.cipher\.version | string | 
action\_result\.data\.\*\.ssl\.tlsext\.\*\.id | numeric | 
action\_result\.data\.\*\.ssl\.tlsext\.\*\.name | string | 
action\_result\.data\.\*\.ssl\.versions\.\*\. | string | 
action\_result\.data\.\*\.title | string | 
action\_result\.data\.\*\.transport | string | 
action\_result\.data\.\*\.port | numeric |  `port` 
action\_result\.data\.\*\.\_shodan\.options | string | 
action\_result\.data\.\*\.\_shodan\.module | string | 
action\_result\.data\.\*\.data | string | 
action\_result\.data\.\*\.asn | string |  `asn` 
action\_result\.data\.\*\.timestamp | string | 
action\_result\.data\.\*\.ip | string | 
action\_result\.summary\.results | numeric | 
action\_result\.summary\.hostnames\.\*\. | string | 
action\_result\.summary\.country | string | 
action\_result\.summary\.open\_ports | string | 
action\_result\.data\.\*\.isp | string | 
action\_result\.data\.\*\.org | string | 
action\_result\.data\.\*\.hash | numeric | 
action\_result\.data\.\*\.ip\_str | string |  `ip` 
action\_result\.data\.\*\.\_shodan\.crawler | string | 
action\_result\.data\.\*\.location\.city | string | 
action\_result\.data\.\*\.location\.area\_code | numeric | 
action\_result\.data\.\*\.location\.postal\_code | string | 
action\_result\.data\.\*\.location\.dma\_code | numeric | 
action\_result\.data\.\*\.location\.region\_code | string | 
action\_result\.data\.\*\.location\.country\_code | string | 
action\_result\.data\.\*\.location\.country\_name | string | 
action\_result\.data\.\*\.location\.country\_code3 | string | 
action\_result\.data\.\*\.location\.latitude | numeric | 
action\_result\.data\.\*\.location\.longitude | numeric | 
action\_result\.status | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'query domain'
Search Shodan\.io for discovered service info

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**domain** |  required  | Domain to query | string |  `domain` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.domain | string |  `domain` 
action\_result\.data\.\*\.ip\_str | string |  `ip` 
action\_result\.data\.\*\.product | string | 
action\_result\.data\.\*\.cpe | string | 
action\_result\.data\.\*\.device\_type | string | 
action\_result\.data\.\*\.os | string | 
action\_result\.data\.\*\.transport | string | 
action\_result\.data\.\*\.port | numeric |  `port` 
action\_result\.data\.\*\.\_shodan\.module | string | 
action\_result\.data\.\*\.data | string | 
action\_result\.data\.\*\.asn | string |  `asn` 
action\_result\.data\.\*\.timestamp | string | 
action\_result\.data\.\*\.ssl\.cert\.issued | string | 
action\_result\.data\.\*\.ssl\.cert\.issuer\.C | string | 
action\_result\.data\.\*\.ssl\.cert\.issuer\.O | string | 
action\_result\.data\.\*\.ssl\.cert\.issuer\.CN | string | 
action\_result\.data\.\*\.ssl\.cert\.issuer\.OU | string | 
action\_result\.data\.\*\.ssl\.cert\.pubkey\.bits | numeric | 
action\_result\.data\.\*\.ssl\.cert\.pubkey\.type | string | 
action\_result\.data\.\*\.ssl\.cert\.serial | numeric | 
action\_result\.data\.\*\.ssl\.cert\.expired | boolean | 
action\_result\.data\.\*\.ssl\.cert\.expires | string | 
action\_result\.data\.\*\.ssl\.cert\.sig\_alg | string | 
action\_result\.data\.\*\.ssl\.cert\.subject\.C | string | 
action\_result\.data\.\*\.ssl\.cert\.subject\.L | string | 
action\_result\.data\.\*\.ssl\.cert\.subject\.O | string | 
action\_result\.data\.\*\.ssl\.cert\.subject\.CN | string | 
action\_result\.data\.\*\.ssl\.cert\.subject\.OU | string | 
action\_result\.data\.\*\.ssl\.cert\.subject\.ST | string | 
action\_result\.data\.\*\.ssl\.cert\.version | numeric | 
action\_result\.data\.\*\.ssl\.cert\.extensions\.\*\.data | string | 
action\_result\.data\.\*\.ssl\.cert\.extensions\.\*\.name | string | 
action\_result\.data\.\*\.ssl\.cert\.extensions\.\*\.critical | boolean | 
action\_result\.data\.\*\.ssl\.cert\.fingerprint\.sha1 | string | 
action\_result\.data\.\*\.ssl\.cert\.fingerprint\.sha256 | string | 
action\_result\.data\.\*\.ssl\.chain\.\*\. | string | 
action\_result\.data\.\*\.ssl\.cipher\.bits | numeric | 
action\_result\.data\.\*\.ssl\.cipher\.name | string | 
action\_result\.data\.\*\.ssl\.cipher\.version | string | 
action\_result\.data\.\*\.ssl\.tlsext\.\*\.id | numeric | 
action\_result\.data\.\*\.ssl\.tlsext\.\*\.name | string | 
action\_result\.data\.\*\.ssl\.versions\.\*\. | string | 
action\_result\.data\.\*\.deprecated\.html\.eol | string | 
action\_result\.data\.\*\.deprecated\.html\.new | string | 
action\_result\.data\.\*\.deprecated\.title\.eol | string | 
action\_result\.data\.\*\.deprecated\.title\.new | string | 
action\_result\.data\.\*\.deprecated\.opts\.pem\.eol | string | 
action\_result\.data\.\*\.deprecated\.opts\.pem\.new | string | 
action\_result\.data\.\*\.deprecated\.opts\.robots\.eol | string | 
action\_result\.data\.\*\.deprecated\.opts\.robots\.new | string | 
action\_result\.data\.\*\.deprecated\.opts\.sitemap\.eol | string | 
action\_result\.data\.\*\.deprecated\.opts\.sitemap\.new | string | 
action\_result\.data\.\*\.total | numeric | 
action\_result\.data\.\*\.ip | numeric | 
action\_result\.data\.\*\.isp | string | 
action\_result\.data\.\*\.org | string | 
action\_result\.data\.\*\.hash | numeric | 
action\_result\.data\.\*\.isakmp\.flags\.commit | boolean | 
action\_result\.data\.\*\.isakmp\.flags\.encryption | boolean | 
action\_result\.data\.\*\.isakmp\.flags\.authentication | boolean | 
action\_result\.data\.\*\.isakmp\.length | numeric | 
action\_result\.data\.\*\.isakmp\.msg\_id | string | 
action\_result\.data\.\*\.isakmp\.version | string | 
action\_result\.data\.\*\.isakmp\.next\_payload | numeric | 
action\_result\.data\.\*\.isakmp\.exchange\_type | numeric | 
action\_result\.data\.\*\.isakmp\.initiator\_spi | string | 
action\_result\.data\.\*\.isakmp\.responder\_spi | string | 
action\_result\.data\.\*\.\_shodan\.crawler | string | 
action\_result\.data\.\*\.domains\.\*\. | string | 
action\_result\.data\.\*\.location\.city | string | 
action\_result\.data\.\*\.location\.area\_code | numeric | 
action\_result\.data\.\*\.location\.postal\_code | string | 
action\_result\.data\.\*\.location\.dma\_code | numeric | 
action\_result\.data\.\*\.location\.region\_code | string | 
action\_result\.data\.\*\.location\.country\_code | string | 
action\_result\.data\.\*\.location\.country\_name | string | 
action\_result\.data\.\*\.location\.country\_code3 | string | 
action\_result\.data\.\*\.location\.latitude | numeric | 
action\_result\.data\.\*\.location\.longitude | numeric | 
action\_result\.data\.\*\.hostnames\.\*\. | string | 
action\_result\.data\.\*\.ssh\.kex\.unused | numeric | 
action\_result\.data\.\*\.ssh\.kex\.languages\.\*\. | string | 
action\_result\.data\.\*\.ssh\.kex\.kex\_follows | boolean | 
action\_result\.data\.\*\.ssh\.kex\.kex\_algorithms\.\*\. | string | 
action\_result\.data\.\*\.ssh\.kex\.mac\_algorithms\.\*\. | string | 
action\_result\.data\.\*\.ssh\.kex\.encryption\_algorithms\.\*\. | string | 
action\_result\.data\.\*\.ssh\.kex\.compression\_algorithms\.\*\. | string | 
action\_result\.data\.\*\.ssh\.kex\.server\_host\_key\_algorithms\.\*\. | string | 
action\_result\.data\.\*\.ssh\.key | string | 
action\_result\.data\.\*\.ssh\.mac | string | 
action\_result\.data\.\*\.ssh\.type | string | 
action\_result\.data\.\*\.ssh\.cipher | string | 
action\_result\.data\.\*\.ssh\.fingerprint | string | 
action\_result\.data\.\*\.info | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary\.results | numeric | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric | 