# Key Points

## IP Addresses ##

### Address Types

<u>Classful</u>  
**Class A** (000-127/8) (GE, but took it back) (most networks, least hosts)  
**Class B** (128-191/16) (balanced)  
**Class C** (192-233/24) (least networks, most hosts)  
**Class D** (224-239) multicasting  
**Class E** (240-255) reserved (nobody cares, don't neet to know)

<u>IPv4 Broadcast</u>  
\- one-to-all  
\- can cause flooding  
\- used by ARP and switch forwarding  
==host bits are set to ones==

<u>IPv6 Anycast</u>  
\- one-to-nearest communication  
\- data is sent to the topologically closest node among a group  
\- standard unicast addresses are assigned to multiple devices  
\- unicast with multiple dests  
==host bits are set to ones==

<u>IPv4 Experimental</u>  
\- Class E  
\- not used publicly  
==240.0.0.0/4==

<u>IPv6 Reserved</u>  
Default Route $\rightarrow$ ::/0  
Unspecified Address $\rightarrow$ ::/128  
#### Common Types
<u>Unicast</u>  
\- 1-1 communication  
\- unique (either locally or globally)

<u>Public</u>  
\- required for internet access  
\- GUA (IPv6) does not need a NAT  
==1.0.0.0/8 to 223.0.0.0/8== (except private, loopback)  
==2000::/3== (which can also look like 2001::/3)

<u>Private</u>  
\- local only--not internet routable  
\- used for addressing within a site or group of sites  
\- can be used for devices that will never need to access another network  
\- (IPv6) not globally routed or translated to a global IPv4 address  
\- many sites use ULAs as a security measure, which is not what ULAs were designed for  
==10.0.0.0/8, 172.16.0.0.0/12, 192.168.0.0/16==  
==FC00::/7== (may also show up as FD00::/7)

<u>Loopback</u>  
\- call to host machine  
\- used to test if TCP/IP works  
==127.0.0.0/8== and ==::1/128==

<u>Link-Local Addresses (LLA)</u>  
\- traffic is one-hop  
\- local to a router  
\- used only for neighbor discovery and next hop configuration  
\- (IPv4) assigned when no IP address is DHCP or statically defined (APIPA)  
==169.254.0.0/16==  
==FE80::/10==

#### Multicasting
<u>IPv4 Multicast</u>  
\- one-to-many or many-to-many communication  
\- source can send data to a group of interested recipients without duplication at the source  
\- routers replicate packets only as needed  
\- dynamic grouping (hosts can leave and join as needed)  
==224-239==

<u>IPv6 Multicast</u>  
\- superset of link-local, a couple of other types of  
==FF00::/8== 

<u>IPv6 Multicast All Groups</u>  
\- All-nodes group: all devices join  
\- All-routers: only routers (auto-joined with enabled with `ipv6 unicast-routing` global config command)  
**Multicast is the key to IPv6:** auto-joins "all nodes" and "all routers" groups

<u>IPv6 Multicast Solicited Node</u>  
\- similar to all nodes  
\- mapped to special ethernet multicast address  
\- the ethernet NIC filters traffic by examining the dest mac address to see if the device is the intended target of the packet
## OSI Model ##
[This video helps](https://www.youtube.com/watch?v=3kfO61Mensg)  
All People Seem To Need Data Processing  
![osi-model-1569501229.gif](images/osi-model-1569501229.gif)

### 1. Physical Layer
**Bits**  
\- last step in encapsulation  
\- the bits are encoded and transmitted between devices  
\- connection can be wired or wireless  

<u>Crossover Cable</u>  
*crossover vs straight-through doesn't matter as much--OS switches the pins programmatically*  
\- host-to-host, switch-to-switch, router-to-router  
\- pairs are switched

<u>Ethernet Straight Through</u>  
\- Host to network  
\- no pins are switched

<u>Rollover</u>  
\- Console to router  
\- Cisco proprietary  
\- pins are inverted
### 2. Data Link Layer ###
**Frames**  
\- accepts a frame from the network medium  
\- de-encapsulates and parses the data  
\- re-encapsulates  
\- forwards it to appropriate next segment  

<u>Logical Link Control (LLC)</u>  
\- communicates between networking software (upper layers) and device hardware (lower layers)  
\- primarily concerned with (de)multiplexing data  
\- handles flow control and error management (except CSMA)  

<u>Media Access Control (MAC)</u>  
\- frame delimiting and recognition  
\- protection against errors, generally by means of generating and checking FCS  
\- control of access to the physical transmission medium  
\- receive/transmit normal frames (CSMA)  
\- half-duplex retransmission and backoff functions  
\- discard malformed frames

#### MAC Addresses ###
<u>MAC Address Assignment</u>  
\- Organizationally Unique Identifier (OUI): 24 bits  
\- Vendor Assigned: 24 bits

<u>Multicast MAC Address</u>  
\- dest only  
\- based on multicast ip address  
IPv4 address $\rightarrow$ ==01-00-5E== (append last 23 bits of ip)  
\- 32 multicast mac to 1 multicast ipv4  
IPv6 address $\rightarrow$ ==33-33== (append last 32 bits of ip)  
\- flooded out to all switch ports (except source port)  
\- not forwarded by the router (unless otherwise configured)  

<u>Content Addressable Memory (CAM)</u>  
\- switches match ports and IP addresses based on the source address  
\- adds source (mac, port, time to live) to MAC table  
\- unicast forwarding (looks at table first to avoid flooding)  
*if broadcast or multicast, flood to all ports except where it came from*

#### Ethernet Frames
<u>Ethernet Frame Fields</u>  
\- 6 bytes: Dest MAC address  
\- 6 bytes: Source MAC address  
\- 2 bytes: Type/length  
\- 46-1500 bytes: Data  
\- 4 bytes: Checksum

**Minimum 64 bytes** (collision detection) $\rightarrow$ Anything less is a runt and dropped  
**Max 1518 bytes** (memory management) $\rightarrow$ Anything more is giant and (can be) error frame

<u>NIC Processing</u>  
\- NIC receives Ethernet frame  
\- if dest address matches device address (in RAM), frame is passed up the layers for de-encapsulation  
\- otherwise, device discards frame

#### Switch Forwarding
\- switches need an IP addresses for remote management from console/VTY

<u>Store and Forward Switching</u>  
*slowest, most secure, most common*  
\- computes CRC immediately after receiving the entire frame  
\- if cyclic redundancy check (CRC) is valid, forward, otherwise drop  
\- if frame is runt or giant, also drop  
\- essential in case of encrypted frames  
\- used in mixed-rate environments

<u>Cut Through Switching</u>  
\- forwarding before the entire frame is received  
\- can lead to forwarding error frames

<u>Fast Forward Switching</u>  
*fastest*  
\- read dest and immediately start forwarding  
\- type of cut-through

<u>Fragment-Free Switching</u>  
*compromise*  
\- receive the first 64 bytes (gaurantee not a runt), then forward  
\- type of cut-through

### 3. Network Layer
**Packets**

<u>Basic Routing</u>  
*ip header (Layer 3) never changes*  
\- Layer 2: source uses the MAC address of the router (discover via ARP) to send packet to gateway  
\- Layer 2: router 1 receives frame and de-encapsulates  
\- Layer 3: determines next dest  
\- Layer 2: determines next MAC address and re-encapsulates (source is now router)  
\- Layer 2: send to next MAC Address (discover via ARP)

<u>Connectionless</u>  
\- ip does not establish a connection before sending, just sends  
\- no control info or pre-notifications needed  
\- if connection-oriented traffic is needed, a different protocol will be used (ex TCP)

<u>Fragmenting</u>  
\- IPs breaks larger packets into pieces that can be transmitted at lower layer MTU  
\- fragmenting causes latency  
\- IPv4 must fragment and reassembly  
\- IPv6 packets cannot be fragmented by anything but the source

### 4. Transport Layer
**Segments**
#### Transmission Control Protocol (TCP)
<u>Connection Oriented</u>  
\- sequencing, acknowledgement, retransmission  
\- flow rate control  
\- TCP three-way handshake

<u>Three Way Handshake</u>
1. client initiates client-to-server session with the server (SYN, SEQ)
2. the server acknowledge session and requests server-to-client session (SEQ, ACK, CTL=SYN, ACK)
3. client acknowledges server to client session (SEQ, ACK, CTL=ACK)

<u>Session Termination</u>
1. client sends FIN
2. server sends ACK and FIN
3. client sends ACK

<u>SACK</u>  
\- if both hosts support SACK, reduces redundant retransmission  
\- Selective acknowledgement allows for the retransmission of just the dropped packet(s)

#### User Datagram Protocol (UDP)
<u>Connectionless</u>  
\- best-effort  
\- no reliability or acknowledgement  
\- little overhead or checking
### 7. Application Layers
**Data**  
\- Session, Presentation, Application  
\- Common applications: HTTP(S), TCP, Mail, TCP/UDP, DNS, DHCP

<u>Email Protocols</u>  
\- TCP-based protocols  
SMTP: used to send mail (port 25)  
POP3 or IMAP: used to receive mail

<u>DHCP Operation (DORA)</u>  
Discover:  client broadcasts to identify DHCP servers (DHCPDISCOVER)  
Offer: DHCP host offers client an available address (first-come, first-serve) (DHCPOFFER)  
Request: from client to accept offer  (DCHPREQUEST)  
Ack: from host to confirm (DHCPACK) or deny (DHCPNAK) assignment

<u>Types of DNS Records</u>  
A: IPv4 end device  
NS: authoritative name server  
Quad-A (AAAA): IPv6 end device  
MX: Mail exchange

<u>File Transfers</u>  
FTP:  control 21, data 20  
SMB: printing

## Well-Known Ports
**20**: FTP data  
**21**: FTP control  
**22**: SSH  
**23**: Telnet  
**25**: SMTP  
**53**: DNS  
**80**: HTTP  
**110**: POP2  
**143**: IMAP  
**443**: HTTPS  