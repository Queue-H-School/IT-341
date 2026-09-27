# Lecture 4: IPv6 Addresses #

**340 Undecillion address space**  
\- genuinely an unfathomable amount of addresses

<u>IPv4 --> IPv6 Transition</u>  
\- Dual stack: devices run bother IPv4 and IPv6 protocols simultaneously  
\- Tunneling: transporting and IPv6 packet over IPv4 network (IPv6 is encapsulated inside IPv4)  
\- Translation: Network Address Translation 64 (NAT64) enable IPv6 devices to communicate with IPv4 devices similar to NAT for IPv4  
*these are only stopgaps; the goal should be native IPv6 communication, but, in reality, IPv4 is very practical for most internal use*

<u>Formatting</u>  
\- 128 bits in an address (called a hextet)  
\- 8 sets of four hex values (separated by :)  
\- drop leading zeroes  
\- double colons should only happen once  
Ex: 2001:0db8:0000:1111:0000:0000:0000:0200 → 2001:db8:0:1111::200

<u>IPv6 Prefixes</u>  
\- can be as many as /128  
\- reccomended to use a 64-bit interface id makes Stateless address autoconfig (SLAAC) and subnetting easier

<u>IPv6 Casting</u>  
Unicast: identifies 1 unique interface  
Multicast: 1 packet goes to multiple interface  
Anycast: 1 unicast address can be assigned to multiple devices  
\- an anycast packet is routed to the nearest device with the address  
*No broadcasting--can spam network*

<u>Anycast</u>  
\- load balancing  
\- go to the nearest server

### Types of IPv6 Addresses ##

<u>Global Unique Addresses</u>  
\- equivalent to an IPv4 public address  
\- required for internet access  
\- no NAT needed

<u>Link-Local Addresses (LLA)</u>  
\- traffic is one-hop  
\- local to a router  
\- routers can have multiple LLA (can be the same, somehow)  
\- fe80::/10 range

<u>Unique Local Addresses</u>  
*range c00::/7 to fdff::/7*  
\- similar to RFC 1918 private IPv4 addresses  
\- used for addressing within a site or group of sites  
\- can be used for devices that will never need to access another network  
\- not globally routed or translated to a global IPv4 address  
*many sites use RFC 1918 addresses as a security measure, which is not what ULAs were designed for*

<u>IPv6 Global Unicast Addresses (GUAs)</u>  
\- globally unique and routable on the IPv6 internet  
\- /3 prefix (2000::/3)  
\- begin with a decimal of 2 or 3

### IPv6 Multicast ###
*a multicast group consists of receivers wanting to receive a particular data stream*

<u>Common Groups</u>  
\- All-nodes group: all devices join  
\- All-routers: only routers (auto-joined with enabled with `ipv6 unicast-routing` global config command)  
**Multicast is the key to IPv6:** auto-joins "all nodes" and "all routers" groups

<u>Solicited Node</u>  
\- similar to all nodes  
\- mapped to special ethernet multicast address  
\- the ethernet NIC (network interface card) filters traffic by examining the dest mac address to see if the device is the intended target of the packet
