# Lecture 2: Basic Switch and End Device Configuration #

<u>Machine Architecture</u></br>
\- User interaction on GUI \-\-> Kernel interprets to machine code \-\-> Hardware reacts</br>
\- GUIs make computers available to the public, and CLI commands bridge the gap between human and OS</br>

<u>Access methods</u></br>
1 Set up the device to managed via a physical connection to the console</br>
2 SSH (encrypted, port 22) or Telnet (cleartext, port 23)</br>

<u>Terminal Emulation</u></br>
\- User mode (>) and command mode (#) \*god mode\*</br>
\- Global config (change across deviec), line config (change console, SSH, Telnet, or AUX), interface config (config switch port or router interface)</br>

<u>Naming Guideline</u></br>
\- begin with letter</br>
\- no spaces</br>
\- end with letter/digit</br>
\- use only [a\-zA\-Z0\-9\-]</br>
\- less than 64 chars</br>

*for the love of god, use a good password*

<u>IP Addresses</u> </br>
\- IPv4: 255.255.255.255</br>
\- IPv6 *whoops, ran out of IPv4*: ffff:ffff:ffff:ffff:ffff:ffff:ffff:ffff (leading zeroes are dropped, sometimes resulting in ::)</br>
\- A subnet mask is a 32\-bit value that differentiates the network portion of the address from the host portion.</br>
\- IP address + subnet idenitifies a device</br>

<u>Switch Virtual Interface (SVI) Conf</u></br>
\- to access switch remotely, IP address and subnet mask must be configured on SVI</br>
**To Configure:**</br>
1 `# interface vlan 1`</br>
2 ip address `*ip\-address* *subnet\-mask*` to assign IPv4</br>
3 `shutdown` to enable virtual interface</br></br>

## Commands ##

<u>Command Synax</u></br>
**commands and keywords entered literally**</br>
*arguments for which you supply values*</br>
[optional element]</br>
{required element}</br>
[requires x {choose y | or z}]</br>

*conf for configure*

<u>Configuration</u></br>
`show` same as cat</br>
`> enable` sends to privileged mode</br>
`exit` brings config mode back up the tree</br>
`# configure terminal` moves in and out of global configuration mode</br>
`# line *management\-type*` changes configuration to line config</br>
`# interface *management\-type*` changes configuration mode to interface config</br>
`# reload` device restart (wipes ram)</br>


<u>Virtual Teletype (VTY)</u></br>
`# line vty 0 15` sets up 16 (numbered) vty lines</br>

<u>Security</br>
</u>`# hostname *new\-hostname*` changes the hostname to "new\-hostname"</br>
`# password *password*` changes the device's password to "password"</br>
`# enable secret *password*` requires the password "password" to escalate privileges</br>
`# service password\-encryption` encrypts passwords</br>
`# banner motd *message*` sets sercurity banner message to message (requires start and end chars)</br>

<u>Config Types</u></br>
`# show running\-config` displays current config (in ram) </br>
`# show startup\-config` displays saved conf stored in NVRAM</br>
`# copy running\-config startup\-config` saves running\-config to start\-up config</br>
`# erase startup\-config` erases startup\-config (resets to factory settings)</br>

<u>Export Setting to .txt</u></br>
1 In terminal emulator, assign name and file location to save log file</br>
2 `# show running\-config` or `# show startup\-config` to send settings to log file</br>