# OSI Layer 3: Network Layer #
\- responsible for addressing and routing</br>
\- encapsulates and de-encapsulates data</br>

<u>IP Encapsulation</u></br>
\- encapsulates the transport layer segment</br>
\- can use either IPv4 or IPv6 and not impact the layer 4 segment</br>
\- IP addressing does not change from source to dest (except NAT)</br>
\- all layer 3 devices will examine an IP packet</br>

## Characteristics of IP ##
<u>Connectionless</u></br>
\- ip does not establish a connection before sending, just sends</br>
\- no control info or pre-notifications needed</br>
\- if connection-oriented traffic is needed, a different protocol will be used (ex TCP)</br>

<u>Best Effort</u></br>
\- IP does not guarantee delivery</br>
\- packet is transmitted as quickly and efficiently as possible</br>
\- error management falls to other protocols</br>
\- no mechanism to resend data (some packets may be lost enroute)</br>
\- no acknowledgements (low overhead)</br>
\- re: connectionless</br>

<u>Media Independent</u></br>
\- does not care what happens at the data link level (connection type doesn't matter)</br>
\- cannot fix undelivered or corrupt packets</br>
\- IP has to break packets into pieces to accommodate lower layer Maximum Transmission Unit (MTU)</br>

<u>Fragmenting</u></br>
\- IPs breaks larger packets into pieces that can be transmitted at lower layer MTU</br>
\- fragmenting causes latency</br>
\- IPv4 must fragment and reassembly</br>
\- IPv6 packets cannot be fragmented by anything but the source</br>

<u>IPv4 Packet Header</u></br>
\- 20 bytes for IPv4 network</br>
![ipv4-header.png](images/ipv4-header.png)</br>
\- version 4</br>
\- total length $\rightarrow$ header + data</br>
\- fragment offset $\rightarrow$ helps reassembly by indicating which bytes are present</br>
\- time to live $\rightarrow$ prevents infinite looping (default 255, decremented by each router that processes)</br>
\- checksum $\rightarrow$ re-calculated after time to live is updated</br>

<u>IPv6 Packet Header</u></br>
\- 40 bytes (simplified but not smaller--larger ip addresses)</br>
\- no fragmenting (only source can fragment)</br>
\- no checksum</br>
![ipv6-header.png](images/ipv6-header.png)</br>
\- version 6</br>
\- payload length $\rightarrow$ length of the data portion</br>
\- next header $\rightarrow$ protocol type</br>
\- hop limit $\rightarrow$ time to live</br>
\- extension header $\rightarrow$ optional information used for fragmentation, security, mobility support</br>
*due to re-assembly and checksum, IPv6 is faster than IPv4*</br>

## Host Routing ##
<u>Forwarding Determination</u></br>
\- packets are always created at source</br>
\- layer 3 (network) responsible for routing</br>
\- loopback $\rightarrow$ 127.0.0.0 or ::1</br>
\- go to local or remote hosts (tell difference based on subnet mask)</br>
*remote dests go to "default gate"*</br>

<u>Default Gateway (DGW)</u></br>
\- just the IP address of the nearest router</br>
\- must be on the same subnet as LAN (sometimes highest valid host)</br>
\- configured statically or through DHCP</br>

<u>Host Routing Tables</u></br>
\- default route is the default gateway</br>
\- interface list $\rightarrow$  all potential interfaces and MAC addresses</br>

<u>Basic Routing</u></br>
*ip header (Layer 3) never changes*</br>
\- Layer 2: source uses the MAC address of the router (discover via ARP) to send packet to gateway</br>
\- Layer 2: router 1 receives frame and de-encapsulates</br>
\- Layer 3: determines next dest </br>
\- Layer 2: determines next MAC address and re-encapsulates (source is now router)</br>
\- Layer 2: send to next MAC Address (discover via ARP)</br>

<u>Router Routing Table</u></br>
Directly Connected $\rightarrow$ routes are automatically added (when interface is active)</br>
Remote $\rightarrow$ must be learned either statically or dynamically (DHCP)</br>
Remote (Default Route) $\rightarrow$ used when there is no match in the routing table</br>
`show ip route` to display connections
