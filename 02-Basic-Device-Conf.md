# Lecture 2: Basic Device Configuration

<u>Machine Architecture</u>  
\- User interaction on GUI \-\-> Kernel interprets to machine code \-\-> Hardware reacts  
\- GUIs make computers available to the public, and CLI commands bridge the gap between human and OS

<u>Access methods</u>  
1. Set up the device to managed via a physical connection to the console  
2. SSH (encrypted, port 22) or Telnet (cleartext, port 23)

<u>Terminal Emulation</u>  
\- User mode (>) and command mode (#) \*god mode\*  
\- Global config (change across deviec), line config (change console, SSH, Telnet, or AUX), interface config (config switch port or router interface)

<u>Naming Guideline</u>  
\- begin with letter  
\- no spaces  
\- end with letter/digit  
\- use only [a\-zA\-Z0\-9\-]  
\- less than 64 chars

*for the love of god, use a good password*

<u>IP Addresses</u>  
\- IPv4: 255.255.255.255  
\- IPv6 *whoops, ran out of IPv4*: ffff:ffff:ffff:ffff:ffff:ffff:ffff:ffff (leading zeroes are dropped, sometimes resulting in ::)  
\- A subnet mask is a 32\-bit value that differentiates the network portion of the address from the host portion.  
\- IP address + subnet idenitifies a device

<u>Switch Virtual Interface (SVI) Conf</u>  
\- to access switch remotely, IP address and subnet mask must be configured on SVI  
**To Configure:**  
1. `# interface vlan 1`  
2. ip address `ip-address subnet-mask` to assign IPv4  
3. `shutdown` to enable virtual interface

## Commands ##

<u>Command Synax</u>  
**commands and keywords entered literally**  
*arguments for which you supply values*  
\[optional element\]  
{required element}  
\[requires x {choose y | or z}\]  
<u></u>  
*conf for configure*

<u>Configuration</u>  
`show` same as cat  
`> enable` sends to privileged mode  
`exit` brings config mode back up the tree  
`# configure terminal` moves in and out of global configuration mode  
`# line management-type` changes configuration to line config  
`# interface management-type* changes configuration mode to interface config  
`# reload` device restart (wipes ram)

<u>Virtual Teletype (VTY)</u>  
`# line vty 0 15` sets up 16 (numbered) vty lines

<u>Security</u>  
`# hostname new-hostname* changes the hostname to "new-hostname"  
`# password password` changes the device's password to "password"  
`# enable secret password` requires the password "password" to escalate privileges  
`# service password-encryption` encrypts passwords  
`# banner motd message` sets security banner message to message (requires start and end chars)

<u>Config Types</u>  
`# show running-config` displays current config (in RAM)  
`# show startup-config` displays saved conf stored in NVRAM  
`# copy running-config startup-config` saves running-config to start-up config  
`# erase startup-config` erases startup\-config (resets to factory settings)

<u>Save Settings</u>  
1. In terminal emulator, assign name and file location to save log file  
2. `# show running-config` or `# show startup-config` to send settings to log file