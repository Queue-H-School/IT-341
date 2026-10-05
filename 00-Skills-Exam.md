# Skills Exam
## Device Config ##
<u>Basic Terminal Setup</u>  
`> enable` switch to exec mode  
`# configure terminal`  
`(config)# hostname name` change hostname  
`(config)# no ip domain-lookup` disable DNS lookup to prevent interpreting incorrect commands as hostnames  
`(config)# enable secret password` protects privileged EXEC mode with password "password"

<u>Protect Console</u>  
`(config)# line con 0` switch to console config  
`(config-line)# password password` protect console access with password "password"  
`(config-line)# login`  
`(config-line)# exit`

<u>Interface Config</u>  
\- VLAN 1 for switches and Gigabit/Ethernet for routers and PCs  
`(config)# interface interface`switch to interface config  
`(config-if)# ip address address` configure ip address  
`(config-if)# ipv6 address address/prefix` configure ipv6 address  
`(config-if)# ipv6 unicast routing` enable IPv6 unicast routing  
`(config-if)# no shut`  keep interface up  
`(config-if)# exit`

<u>Final Touches</u>  
`(config)# banner motd #Unauthorized access is prohibited.#` adds access banner  
`(config)# exit`  
`(config)# copy running-config startup-config`

<u>Required Password Commands</u>  
`(config)# enable secret password` protect exec mode  
`(config)# line con 0` move to console config  
`(config-line)# password password` protect console config  
`(config)# service password-encryption` encrypt passwords  

<u>VTY Console</u>  
This article kinda helps: [techrepublic](https://www.techrepublic.com/article/configure-lines-and-vtys-on-cisco-routers/)  
\- virtual teletype  
\- basically like ports you can ssh or telnet into  
\- impacted by line-config mode  
![[cisco-ios-tree.avif]]

## Subnetting ##
<u>Network bits cannot be changed</u>  
Ex: 10.0.0.0/8 $\rightarrow$ network is 10  
Ex: 10.0.0.0/16 $\rightarrow$ network is 10.0.0

<u>Valid Hosts</u>  
\- $2^h - 2$ ($h =$ number of host bits)  
\- the 2 invalid host addresses are when the host bit are all zeroes or all ones (broadcast address)  
\- when host bits are all 0, it indicates the network as a whole--does not point to a host

<u>Number of Subnets</u>  
\- "borrow" from host bits  
\- $2^n =$ number of subnets ($n =$ number of "borrowed" bits)  
Ex: 192.168.1.0/24 $\rightarrow$ 192.168.1.0/26 = add 4 new networks

### Variable Length Subnet Masking (VLSM)
![08fig40.jpg](images/08fig40.jpg)  
[^1]

Use this to practice: [CompSciRocks](https://compsci.rocks/learn/networking/vlsm-practice/)

[^1]: Academy, C., & Cisco Networking Academy Program,  author. (2013). Network Basics Companion Guide / Academy, Cisco. (1st edition). Cisco Press.