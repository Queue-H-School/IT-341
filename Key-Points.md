# Key Points #

## Device Config ##
<u>Initial Set-Up</u></br>
`> enable` switch to exec mode</br>

`# configure terminal`</br>
`(config)# hostname name` change hostname</br>
`(config)# no ip domain-lookup` disable DNS lookup to prevent interpreting incorrect commands as hostnames</br>
`(config)# enable secret password` protects privileged EXEC mode</br>

`(config)# line config 0` switch to line config</br>
`(config-line)# password password` protect console access</br>
`(config-line)# login`</br>
`(config-line)# exit`</br>

`(config)# interface interface`switch to interface config</br>
`(config-if)# ip address address` configure ip address</br>
`(config-if)# ipv6 address address/prefix` configure ipv6 address</br>
`(config-if)# ipv6 unicast routing` enable IPv6 unicast routing</br>
`(config-if)# no shut`</br>
`(config-if)# exit`</br>

`(config)# banner motd #Unauthorized access is prohibited.#` adds access banner</br>
`(config)# exit`</br>
`(config)# copy running-config startup-config`</br>

<u>VTY Console</u></br>
[this article kinda helps](https://www.techrepublic.com/article/configure-lines-and-vtys-on-cisco-routers/)</br>
\- virtual teletype</br>
\- basically like ports you can ssh or telnet into</br>
\- impacted by line-config mode</br>

`# line vty 0 15` sets up 16 (numbered) vty lines</br>

## IP Network Casting ##
More in depth at [Github Gist](https://gist.github.com/MangaD/be346bf566e70773e2836c4a4a0bef6d)

<u>Multicast</u></br>
\- one-to-many or many-to-many communication</br>
\- source can send data to a group of interested recipients without duplication at the source</br>
\- routers replicate packets only as needed</br>
\- dynamic grouping (hosts can leave and join as needed)</br>

<u>Anycast</u></br>
\- one-to-nearest communication (IPv6 only)</br>
\- data is sent to the topologically closest node among a group</br>
\- standard unicast addresses are assigned to multiple devices</br>
\- unicast with multiple dests

<u>Broadcast</u></br>
\- one-to-all (IPv4 only)</br>
\- floods the network</br>

<u>Unicast</u></br>
\- 1-1 communication</br>
\- unique (either locally or globally)

## OSI Model ##

![osi-model-1569501229.gif](images/osi-model-1569501229.gif)

<u>Physical Layer</u></br>
\- last step in encapsulation</br>
\- the bits are encoded and transmitted between devices</br>
\- connection can be wired or wireless</br>

<u>Data Link Layer</u></br>
\- accepts a frame from the network medium</br>
\- de-encapsulates and parses the data</br>
\- re-encapsulates</br>
\- forwards it to appropriate next segment</br>
**Logical Link Control (LLC)** $\rightarrow$ communicates between networking software (upper layers) and device hardware (lower layers)</br>
**Media Access Control (MAC)** $\rightarrow$ responsible for data encapsulation and media access control</br>

## Subnetting ##
<u>Network bits cannot be changed</u></br>
Ex: 10.0.0.0/8 $\rightarrow$ network is 10</br>
Ex: 10.0.0.0/16 $\rightarrow$ network is 10.0.0</br>

<u>Valid Hosts</u></br>
\- $2^h - 2$ ($h =$ number of host bits)</br>
\- the 2 invalid host addresses are when the host bit are all zeroes or all ones (broadcast address)</br>
\- when host bits are all 0, it indicates the network as a whole--does not point to a host</br>

<u>Number of Subnets</u></br>
\- "borrow" from host bits</br>
\- $2^n =$ number of subnets ($n =$ number of "borrowed" bits)</br>
Ex: 192.168.1.0/24 $\rightarrow$ 192.168.1.0/26 = add 4 new networks</br>

![08fig40.jpg](images/08fig40.jpg)</br>
Academy, C., & Cisco Networking Academy Program,  author. (2013). Network Basics Companion Guide / Academy, Cisco. (1st edition). Cisco Press.

## Ethernet Frame ##

<u>MAC Address Assignment</u></br>
\- Organizationally Unique Identifier (OUI): 24 bits</br>
\- Vendor Assigned: 24 bits</br>

<u>Ethernet Frame Fields</u></br>
\- 6 bytes: Dest MAC address</br>
\- 6 bytes: Source MAC address</br>
\- 2 bytes: Type/length</br>
\- 46-1500 bytes: Data</br>
\- 4 bytes: Checksum</br>

**Minimum 64 bytes** (collision detection) $\rightarrow$ Anything less is a runt and dropped</br>
**Max 1518 bytes** (memory management) $\rightarrow$ Anything more is giant and (can be) error frame</br>

<u>NIC Processing</u></br>
\- NIC receives Ethernet frame</br>
\- if dest address matches device address (in RAM), frame is passed up the layers for de-encapsulation</br>
\- otherwise, device discards frame</br>

### MAC Addresses ###

<u>Multicast MAC Address</u></br>
IPv4 address $\rightarrow$ 01-00-5E</br>
IPv6 address $\rightarrow$ 01-00-33-33</br>
\- flooded out to all switch ports (except source port)</br>
\- not forwarded by the router (unless otherwise configured)</br>
\- used as a destination packet only</br>

<u>Content Addressable Memory (CAM)</u></br>
\- switches match ports and IP addresses based on the source address</br>
\- adds source (mac, port, time to live) to MAC table</br>
\- unicast forwarding (looks at table first to avoid flooding)</br>
_if broadcast or multicast, flood to all ports except where it came from_</br>

## Important to Memorize ##

<u>Definitions</u></br>
**Hextet**: set of 4 hexadecimal (hex + tetra)</br>
**NIC**: network interface card</br>

<u>RFC 1918 Private Addressing</u></br>
\- 10.0.0.0/8</br>
\- 172.16.0.0/12 </br>
\- 192.168.0.0/16</br>

<u>RFC 790 Classes</u></br>
**A** (000-127/8) (GE, but took it back) (most networks, least hosts)</br>
**B** (128-191/16) (balanced)</br>
**C** (192-233/24) (least networks, most hosts)**</br>
**D** (224-239) multicasting</br>
**E** (240-255) reserved (nobody cares, don't neet to know)</br>
