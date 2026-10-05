# Key Points

## IP Addresses ##

### Address Types

#### Public  
<u>IPv6 Global Unicast Addresses (GUAs)</u>  
\- globally unique and routable on the IPv6 internet  
\- /3 prefix (2000::/3)  
<u>Global Unique Addresses</u>  
\- equivalent to an IPv4 public address  
\- required for internet access  
\- no NAT needed

#### Private

Experimental

<u>Unique Local Addresses</u>  
\- similar to private IPv4 addresses  
\- used for addressing within a site or group of sites  
\- can be used for devices that will never need to access another network  
\- not globally routed or translated to a global IPv4 address  
*many sites use these as a security measure, which is not what ULAs were designed for*

<u>Loopback</u>  
\- call to host machine  
\- used to test if TCP/IP works

<u>Link-Local</u> ????  
\- commonly known at Automatic Private IP Addressing (APIPA)  
\- used by Windows DCHP if DCHP fails

<u>Link-Local Addresses (LLA)</u>  
\- traffic is one-hop  
\- local to a router  
\- routers can have multiple LLA (can be the same, somehow)  
#### Casting
More in depth at [Github Gist](https://gist.github.com/MangaD/be346bf566e70773e2836c4a4a0bef6d)

<u>Anycast</u>  
\- one-to-nearest communication (IPv6 only)  
\- data is sent to the topologically closest node among a group  
\- standard unicast addresses are assigned to multiple devices  
\- unicast with multiple dests

<u>Broadcast</u>  
\- one-to-all (IPv4 only)  
\- floods the network

<u>Unicast</u>  
\- 1-1 communication  
\- unique (either locally or globally)

##### Multicast
\- one-to-many or many-to-many communication  
\- source can send data to a group of interested recipients without duplication at the source  
\- routers replicate packets only as needed  
\- dynamic grouping (hosts can leave and join as needed)  
\- **Type D: 224-239**

<u>IPv6 Multicast All Groups</u>  
\- All-nodes group: all devices join  
\- All-routers: only routers (auto-joined with enabled with `ipv6 unicast-routing` global config command)  
**Multicast is the key to IPv6:** auto-joins "all nodes" and "all routers" groups

<u>IPv6 Multicast Solicited Node</u>  
\- similar to all nodes  
\- mapped to special ethernet multicast address  
\- the ethernet NIC filters traffic by examining the dest mac address to see if the device is the intended target of the packet

### Ranges
<u>Classful</u>  
Class A (000-127/8) (GE, but took it back) (most networks, least hosts)  
Class B (128-191/16) (balanced)  
Class C (192-233/24) (least networks, most hosts)*  
Class D (224-239) multicasting  
Class E (240-255) reserved (nobody cares, don't neet to know)

<u>Private Addresses</u>   
\- 10.0.0.0/8  
\- 172.16.0.0/12  
\- 192.168.0.0/16

Link-Local: (169.254.0.0/16)  
Loopback: 127.0.0.0/8 (mostly just 127.0.0.1)  

Global Unique Addresses  
Link-Local: fe80::/10 range  
ULA: c00::/7-fdff::/7  
GUA: 2000::/3
## OSI Model ##
[This video helps](https://www.youtube.com/watch?v=3kfO61Mensg)  
All People Seem To Need Data Processing  
![osi-model-1569501229.gif](images/osi-model-1569501229.gif)

### 1. Physical Layer
**Bits**  
\- last step in encapsulation  
\- the bits are encoded and transmitted between devices  
\- connection can be wired or wireless

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
\- receive/transmit normal frames  (CSMA)  
\- half-duplex retransmission and backoff functions  
\- discard malformed frames

#### MAC Addresses ###
<u>MAC Address Assignment</u>  
\- Organizationally Unique Identifier (OUI): 24 bits  
\- Vendor Assigned: 24 bits

<u>Multicast MAC Address</u>  
IPv4 address $\rightarrow$ 01-00-5E  
IPv6 address $\rightarrow$ 01-00-33-33  
\- flooded out to all switch ports (except source port)  
\- not forwarded by the router (unless otherwise configured)  
\- used as a destination packet only

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
80: HTTP  
443: HTTPS  
20: FTP data  
21: FTP control  
53: DNS  
25: SMTP  
110: POP2  
143: IMAP  
23: Telnet  
22: SSH  

## Midterm 1 Review
What is PDU  
Layer 2 switch needs an IP for remote management  
Switch forward (cut through and store and forward)  
know udp and tcp protocols  
link-local, loopback, experimental, etc address types  
multicast mac/ip relationship