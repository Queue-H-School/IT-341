# OSI 5, 6, 7: Application Layers

*do the packet tracer textbook final*  
Session, Presentation, Application

Common applications: HTTP(S), TCP, Mail, TCP/UDP, DNS, DHCP

**Client-server model**

## HTTP and HTTPS
http: protocol or scheme  
www.google.com (server name)  
index.html (filename requested)

\- uses 3-way handshake  
\- server acknowledges with html file  
\- browser display html file

GET: request data  
POST: upload data to server  
PUT: upload data to server??

*HTTP is in plaintext, HTTPS is encrypted*

## Email Protocols
\- TCP-based protocols  
SMTP: used to send mail (port 25)  
POP3 or IMAP: used to receive mail

*email img*

<u>Mail Exchange Record</u>  
\- for external emails  
\- query DNS server (.edu) to receive MX record  
\- if dest email server is down, SMTP "spools" to resend

<u>POP3 and IMAP</u>  
\- retrieves mail from server  
\- checks server every 30-60 secs  
\- POP3 downloads email, then deletes from server (devices out of sync)  
\- IMAP does not delete from server until user manually deletes it

## DNS Service
\- human readable hostnames replace ip addresses  
\- fully qualified domain names (FQDNs)

<u>Types of Records</u>  
A: IPv4 end device  
NS: authoritative name server ?  
Quad-A (AAAA): IPv6 end device  
MX: Mail exchange

DNS servers maintain specific database files for a small portion of the structure

<u>Root Servers</u>  
\- location hidden  
\- top-level domains (.com, .ca, .org, .edu)  
\- massive vulnerability (reflection attack)

<u>Nslookup Command</u>  
\- manually query DNS servers  
\- troubleshoot DNS issues  
\- display default DNS server for your host

## DHCP Assignment
\- port 67  
\- UDP based  
\- time to live can be configured as appropriate

<u>DCHP Usage</u>  
\- auto-configure ip addresses  
\- manages subnets, gatways, and ip addresses  
\- request address from DCHP server, and DCHP assigns from available pool  
\- most networks use both

<u>Static Addressing with DHCP</u>  
\- for devices that don't change  
\- routers, switches, printers, gateways

<u>Operation</u>  
(DORA)  
Discover:  
Offer: DHCP offers client an available address (first-come, first-serve)  
Request: from client to accept offer  
Ack: from host to confirm (or deny) assignment

<u>Address Renewal</u>  
\- at around half of time-to-live, client requests a renewal  
\- if DHCP acknowledges positive, time to live resets

<u>Managing Multiple Requests</u>  
\- if a client receives multiple offers, it must choose  
\- client usually picks the first offer

## File Transfer Protocol (FTP)
\- control plane on port 21  
\- data plane on port 20  
\- TCP-based protocol

<u>Server Message Block (SMB)</u>  
\- downloads remote drive to local  
\- start, authenticate, and terminate sessions  
\- control file and printer access  
\- application sends to receives to/from different device