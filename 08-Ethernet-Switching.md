# Ethernet Switching

Ethernet operates in the data link layer and the physical layer</br>
\- defined in the IEEE 802 standards</br>

<u>Ethernet Frame Fields</u></br>
\- 6 bytes: Dest MAC address</br>
\- 6 bytes: Source MAC address</br>
\- 2 bytes: Type/length</br>
\- 46-1500 bytes: Data</br>
\- 4 bytes: Checksum</br>

**Minimum 64 bytes** (collision detection) $\rightarrow$ Anything less is a runt and dropped</br>
**Max 1518 bytes** (memory management) $\rightarrow$ Anything more is giant and (can be) error frame</br>

## MAC Addresses ##
*Every MAC address is globally unique*</br>
\- can be programmatically spoofed</br>

<u>MAC Address Assignment</u></br>
\- Organizationally Unique Identifier (OUI): 24 bits</br>
\- Vendor Assigned: 24 bits</br>

<u>NIC Processing</u></br>
\- NIC receives Ethernet frame</br>
\- if dest address matches device address (in RAM), frame is passed up the layers for de-encapsulation</br>
\- otherwise, device discards frame</br>

_BUM (broadcast, unicast, multicast)_</br>

<u>Unicast MAC Address</u></br>
\- Standard MAC address (globally unique)</br>
\- identified and matched with IP via ARP</br>
\- source address in frame is always unicast</br>

<u>Broadcast MAC Address</u></br>
\- received and processed by every device on the Ethernet LAN</br>
\- dest broadcast MAC address is FF-FF-FF-FF-FF-FF</br>
\- not forwarded by a router</br>
\- if the encapsulated data is an IPv4 broadcast, then all host on the local network will receive and process the packet</br>

<u>Multicast MAC Address</u></br>
IPv4 address $\rightarrow$ 01-00-5E</br>
IPv6 address $\rightarrow$ 01-00-33-33</br>
\- flooded out to all switch ports (except source port)</br>
\- not forwarded by the router (unless otherwise configured)</br>
\- used as a destination packet only</br>

## MAC Address Table
\- Switches learn based on source address of the Ethernet frame</br>
\- hubs are dumb and don't learn anything</br>

<u>Content Addressable Memory (CAM)</u></br>
\- switches match ports and IP addresses based on the source address</br>
\- adds source (mac, port, time to live) to MAC table</br>
\- unicast forwarding (looks at table first to avoid flooding)</br>
_if broadcast or multicast, flood to all ports except where it came from_</br>

<u>Unknown Unicast Flooding</u></br>
\- if the dest address is not in CAM, switch floods to all ports except source</br>
\- even goes to known ports in case they are attached to a switch (multiple IPs can come from the same port)</br>
