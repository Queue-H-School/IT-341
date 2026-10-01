# Basic Network Security

<u>Bad Actor Goals</u>  
\- information theft  
\- data loss  
\- identity theft  
\- disruption of service

<u>Vulnerability Types</u>  
\- technical vulnerability (os, equipment, requirement vulnerabilities)  
\- poor configuration (weak passwords, no updates, misconfiguration)  
\- bad security policies (weak access controls, poor authentication)

<u>Phsyical Security</u>  
\- accessible hardware (theft, implantation, or listening)  
\- environmental threats (flooding, temperature)  
\- electrical threats (voltage spike, brownout, blackout)  
\- poor maintenance (lack of spare part, poor cabling, poor labeling, electrostatic discharge)

## Types of Malware
\- virus  
\- worm  
\- trojan horse

<u>Reconnaissance Attacks</u>  
\- discovery and mapping of system  
\- constant cycle (to maintain and upgrade access)  
\- first using publicly available info

<u>Access Attacks</u>  
\- manipulation/theft of data  
\- system access or admin access  
\- brute force password  
\- dictionary attack ??  
\- trust exploitation  
\- port redirection  
\- man-in-the-middle (intercepted packets)

<u>Denial of Service</u>  
\- disables or corrupts networks  
\- DoS or defacement  
\- DDoS uses a botnet from command and control

## Mitigations
<u>Defense in Depth</u>  
\- isolation and segmentation to isolate potential damage  
\- separate servers, VPN, firewall

 <u>Backups</u>  
 \- frequency: according to security policy  
 \- storage: protect and validate backups

<u>Updates</u>  
\- updating and patching is critical  
\- upgrading can create new vulnerabilities

## AAA: Authentication, Authorization, Accounting
\- access control  
\- useful in large networks

<u>Authentication</u>  
\- password  
\- prove you are who you say you are

<u>Authorization</u>  
\- prove that you are permitted access  
\- account-based controls  
\- access policies

<u>Accounting</u>  
\- record-keeping  
\- timestamp, userid, actions  
\- like github in developing

## Firewalls
\- authorization  
\- on both end devices and servers  
\- devices outside the firewall "outside the DMZ" and are isolated from the rest of the system

<u>Packet Filtering</u>  
\- prevent or allow based on IP/MAC address  
\- can be port-based

<u>Application Filtering</u>  
\- prevents application type  
\- even if the port is disguised

<u>URL Filters</u>  
\- blacklisted URLS  
\- prevents social media, violence, etc

<u>Stateful Packet Inspection (SPI)</u>  
\- incoming packets must have a legitimate response to a request from an internal host  
\- unsolicited packets are blocked unless whitelisted  
\- helps filter out DoS

## Endpoint Security
\- adblockers, firewalls, passwords

<u>Cisco Autosecure</u>  
\- automates basic default security policies  
\- username and password specifications  
\- port filtering  
\- blocks consecutive failed attempts (bruteforce, dictionary)

<u>Disable Unused Ports/Devices</u>  
\- unneeded ports and unnattended devices are vulnerabilities  
\- networks should be incredibly minimal
## Enable SSH
\- encrypted remote session (telnet is plaintext)