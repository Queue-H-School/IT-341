# Ethernet Switching

Ethernet operates in the data link layer and the physical layer  
\- defined in the IEEE 802 standards

<u>Ethernet Frame Fields</u>  
\- 8 bytes: Preamble and SFD (added at the physical layer)  
\- 6 bytes: Dest MAC address  
\- 6 bytes: Source MAC address  
\- 2 bytes: Type/length  
\- 46-1500 bytes: Data  
\- 4 bytes: Checksum

**Minimum 64 bytes** (collision detection) $\rightarrow$ Anything less is a runt and dropped  
**Max 1518 bytes** (memory management) $\rightarrow$ Anything more is giant and (can be) error frame

## MAC Addresses ##
*Every MAC address is globally unique*  
\- can be programmatically spoofed

<u>MAC Address Assignment</u>  
\- Organizationally Unique Identifier (OUI): 24 bits  
\- Vendor Assigned: 24 bits

<u>NIC Processing</u>  
\- NIC receives Ethernet frame  
\- if dest address matches device address (in RAM), frame is passed up the layers for de-encapsulation  
\- otherwise, device discards frame

_BUM (broadcast, unicast, multicast)_

<u>Unicast MAC Address</u>  
\- Standard MAC address (globally unique)  
\- identified and matched with IP via ARP  
\- source address in frame is always unicast

<u>Broadcast MAC Address</u>  
\- received and processed by every device on the Ethernet LAN  
\- dest broadcast MAC address is FF-FF-FF-FF-FF-FF  
\- not forwarded by a router  
\- if the encapsulated data is an IPv4 broadcast, then all host on the local network will receive and process the packet

<u>Multicast MAC Address</u>  
IPv4 address $\rightarrow$ 01-00-5E  
IPv6 address $\rightarrow$ 01-00-33-33  
\- flooded out to all switch ports (except source port)  
\- not forwarded by the router (unless otherwise configured)  
\- used as a destination packet only
## MAC Address Table
\- Switches learn based on source address of the Ethernet frame  
\- hubs are dumb and don't learn anything

<u>Content Addressable Memory (CAM)</u>  
\- switches match ports and IP addresses based on the source address  
\- adds source (mac, port, time to live) to MAC table  
\- unicast forwarding (looks at table first to avoid flooding)  
_if broadcast or multicast, flood to all ports except where it came from_

<u>Unknown Unicast Flooding</u>  
\- if the dest address is not in CAM, switch floods to all ports except source  
\- even goes to known ports in case they are attached to a switch (multiple IPs can come from the same port)

## Forwarding ##
<u>Store and Forward Switching</u>  
*most common*  
\- computes CRC immediately after recieving the entire frame  
\- if cyclic redunancy check (CRC) is valid, forward, otherwise drop  
\- if frame is runt or giant, also drop  
\- essential in case of encrypted frames  
*used in mixed-rate environments*

<u>Cut Through Switching</u>  
\- determine flood or direct forward first  
\- read dest and immediately start forwarding  
\- can lead to forwarding error frames

<u>Fragment-Free Switching</u>  
\- recieve the first 64 bytes (gaurantee not a runt)  
\- then foward
