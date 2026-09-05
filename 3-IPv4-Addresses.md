# Lecture 3: IPv4 Address Structure #

*Make sure you can easily convert to/from binary, hex, and dec*

<u>IPv4 Addresses</u></br>
\- 4 bytes: 32 bits</br>
\- Written in dotted decimal format (ex: 128.32.32.97)</br>
\- Max FF:FF:FF:FF</br>

<u>IPv6 Addresses</u></br>
\- 4 *hexbits*: 129 bits</br>
\- written in hex (ex: B:F9:9023:F01:F342:324A::1000)</br>
\- Max FFFF:FFFF:FFFF:FFFF:FFFF:FFFF:FFFF:FFFF</br>

<u>Network and Host Portions</u></br>
\- Depends on the subnet mask (no way to tell which is which without it)

<u>Subnet Mask</u></br>
\- Subnet mask & IPv4 = network portion **double check this**</br>
\- Set of ones, then a set of zeroes (just determines length of host portion)</br>
\- Fills greatest to least</br>
Ex: 1111 1111 1111 0000 or 1111 0000 0000 0000</br>

<u>Prefix Length</u></br>
\- indicates the length of the subnet mask</br>
\- prefix of 30 indicates 30 bits of ones for subnet mask</br>
\- notation is \<ip address\>/X
\- subnet mask cannot be longer than the ip address

**Example: Prefix length of 30**</br>
255.255.255.252  
1111 1111 1111 1111 1111 1111 1111 1100

### IP Assignment ###

<u>Reserved host addresses</u></br>
\- host addresses cannot be all zeroes or all ones</br>
\- all ones is the broadcast address</br>

<u>RFC 1918: private IP addresses</u></br>
*internal use, no restrictions</br>*
*no internet routing</br>*
\- 10.0.0.0/8</br>
\- 172.16.0.0/12 </br>
\- 192.168.0.0/16</br>

<u>Link-Local:</u></br>
\- self-assigned addresses</br>
\- commonly known at Automatic Private IP Addressing (APIPA)
\- used by Windows DCHP if DCHP fails

<u>Legacy RFC 790 (1981)</u></br>
IPv4 address classes (very wasteful)</br>
**Class A (000-127) (GE, but took it back)</br> (most networks, least hosts)</br>
Class B (128-191) (balanced)</br>
Class C (192-233) (least networks, most hosts)**</br>
Class D (224-239) multicasting</br>
Class E (240-255) reserved (nobody cares, don't neet to know)</br>

<u>Modern Assignment</u></br>
\- Internet Assigned Numbers Authority (IANA) manages and allocates blocks of addresses to 5 Regional Internet Registries (RIRs)</br>
\- RIRs are responsible for allocating IP addresses to ISPs</br>
\- ISPs provide address blocks to smaller ISPs and organizations</br>


<u>Loopback:</u></br>
\- 127.0.0.0/8 (mostly just 127.0.0.1)</br>
\- used to test if TCP/IP works</br>

### Types of IPv4 'Cast ###

**Unicast**: one to one transmission</br>
**Broadcast**: sends packet to all other hosts (all ones host address)</br>
\- broadcasting is still unique to the network</br>
**Multicast**: sends packet to an address that multiple devices can recieve</br>
\- can be in multiple multicast groups</br>

<u>Network Addresses Translation (NAT)</u></br>
\- typically enabled on the edge router connecting to the internet</br>

<u>Network Segmentation</u>
\- mostly boradcasts or multicasts
\- switches propagate, router stops
\- broadcasts are only propagated within a specific domain (that is controlled by a single router interface)

<u>Large Broadcast Domain Problems</u></br>
\- hosts can generate excessive broadcasts and negatively affect the network
\- so, reduce size of network domain (subnetting)
ex: divide 172.16.0.0./16 into 172.16.0.0/24 and 172.16.1.0/24 (200 users each)
\- divide by location, function, or device type
