# OSI 5, 6, 7: Application Layers

\- Session, Presentation, Application  
\- Common applications: HTTP(S), TCP, Mail, TCP/UDP, DNS, DHCP

<u>Peer to Peer</u>  
\- different from client-server and point-to-point  
\- a computer may be client for one interact and server for another  
\- common with printers and file sharing

## HTTP and HTTPS
*HTTP is in plaintext, HTTPS is encrypted*

<u>1. Interpret URL</u>  
http: protocol or scheme  
www.google.com (server name)  
index.html (filename requested)

<u>2. Check with DNS Server</u>  
\- uses 3-way handshake  
\- server acknowledges with html file 

<u>3. Display file</u>  
\- browser displays the html file

<u>Common Message Types</u>  
GET: request data  
POST: modify and update data  
PUT: create and override data

## Email Protocols
\- TCP-based protocols  
SMTP: used to send mail (port 25)  
POP3 or IMAP: used to receive mail

![[email-diagram.png]]

<u>Mail Exchange (MX) Record</u>  
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
NS: authoritative name server  
Quad-A (AAAA): IPv6 end device  
MX: Mail exchange

<u>Message Format</u>  
\- question: question for the name server  
\- answer: resource records responds with IP address  
\- authority: resource records points to an authority  
\- additional: resource records holds additional information

<u>DNS Hierarchy</u>  
\- DNS servers maintain specific database files for a small portion of the structure  
\- each portion of the url is mapped to a more specific server

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

<u>DHCP Usage</u>  
\- auto-configure ip addresses  
\- manages subnets, gateways, and ip addresses  
\- request address from DHCP server, and DHCP assigns from available pool  
\- most networks use both

<u>Static Addressing with DHCP</u>  
\- for devices that don't change  
\- routers, switches, printers, gateways

<u>Operation (DORA)</u>  
Discover:  client broadcasts to identify DHCP servers (DHCPDISCOVER)  
Offer: DHCP host offers client an available address (first-come, first-serve) (DHCPOFFER)  
Request: from client to accept offer  (DCHPREQUEST)  
Ack: from host to confirm (DHCPACK) or deny (DHCPNAK) assignment

<u>Address Renewal</u>  
\- at around half of TTL, client requests a renewal  
\- if DHCP acknowledges positive, TTL resets

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