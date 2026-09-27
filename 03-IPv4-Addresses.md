# Lecture 3: IPv4 Address Structure #

*Make sure you can easily convert to/from binary, hex, and dec*

<u>IPv4 Addresses</u>  
\- 4 bytes: 32 bits  
\- Written in dotted decimal format (ex: 128.32.32.97)  
\- Max FF:FF:FF:FF

<u>IPv6 Addresses</u>  
\- 4 *hexbits*: 128 bits  
\- written in hex (ex: B:F9:9023:F01:F342:324A::1000)  
\- Max FFFF:FFFF:FFFF:FFFF:FFFF:FFFF:FFFF:FFFF

<u>Network and Host Portions</u>p  
\- Depends on the subnet mask (no way to tell which is which without it)

<u>Subnet Mask</u>  
\- Subnet mask & IPv4 = network portion  
Ex: 192.168.30.154 & /24 = 192.168.30.0  
\- Set of ones, then a set of zeroes (just determines length of host portion)  
\- Fills greatest to least  
Ex: 1111 1111 1111 0000 or 1111 0000 0000 0000

<u>Prefix Length</u>  
\- indicates the length of the subnet mask  
\- prefix of 30 indicates 30 bits of ones for subnet mask  
\- notation is \<ip address\>/X  
\- subnet mask cannot be longer than the ip address

**Example: Prefix length of 30**  
255.255.255.252  
1111 1111 1111 1111 1111 1111 1111 1100  
**Example: Prefix Length of 24**  
255.255.255.0  
1111 1111 1111 1111 1111 1111 0000 0000

## IP Assignment ##

<u>Reserved host addresses</u>  
\- host addresses cannot be all zeroes or all ones  
\- all ones is the broadcast address

<u>RFC 1918: private IP addresses</u>  
**internal use, no restrictions  
no internet routing**  
\- 10.0.0.0/8  
\- 172.16.0.0/12  
\- 192.168.0.0/16

<u>Link-Local:</u>  
\- self-assigned addresses (169.254.0.0/16)  
\- commonly known at Automatic Private IP Addressing (APIPA)  
\- used by Windows DCHP if DCHP fails

<u>Legacy RFC 790 (1981)</u>  
IPv4 address classes (very wasteful)  
**Class A (000-127/8) (GE, but took it back) (most networks, least hosts)  
Class B (128-191/16) (balanced)  
Class C (192-233/24) (least networks, most hosts)**  
Class D (224-239) multicasting  
Class E (240-255) reserved (nobody cares, don't neet to know)

<u>Modern Assignment</u>  
\- Internet Assigned Numbers Authority (IANA) manages and allocates blocks of addresses to 5 Regional Internet Registries (RIRs)  
\- RIRs are responsible for allocating IP addresses to ISPs  
\- ISPs provide address blocks to smaller ISPs and organizations

<u>Loopback</u>  
\- 127.0.0.0/8 (mostly just 127.0.0.1)  
\- used to test if TCP/IP works

## Types of IPv4 'Cast ##

**Unicast**: one to one transmission  
\- can be destination or source  
**Broadcast**: sends packet to all other hosts (all ones host address)  
\- broadcasting is still unique to the network  
\- only a destination address  
**Multicast**: sends packet to an address that multiple devices can recieve  
\- can be in multiple multicast groups  
\- only a destination address  
\- Class D  
\- always starts with 224

<u>Network Addresses Translation (NAT)</u>  
\- typically enabled on the edge router connecting to the internet

<u>Network Segmentation</u>  
\- mostly broadcasts or multicasts  
\- switches propagate, router stops  
\- broadcasts are only propagated within a specific domain (that is controlled by a single router interface)

<u>Large Broadcast Domain Problems</u>  
\- hosts can generate excessive broadcasts and negatively affect the network  
\- so, reduce size of network domain (subnetting)  
ex: divide 172.16.0.0./16 into 172.16.0.0/24 and 172.16.1.0/24 (200 users each)  
\- divide by location, function, or device type
