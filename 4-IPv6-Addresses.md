# Lecture 4: IPv6 Addresses #

**340 Undecillion address space**</br>
\- genuinely an unfathomable amount of addresses</br>

<u>IPv4 --> IPv6 Transition</u></br>
\- Dual stack: devices run bother IPv4 and IPv6 protocols simultaneously</br>
\- Tunneling: transporting and IPv6 packet over IPv4 network (IPv6 is encapsulated inside IPv4)</br>
\- Translation: Network Address Translation 64 (NAT64) enable IPv6 devices to communicate with IPv4 devices similar to NAT for IPv4</br>
*these are only stopgaps, the goal should be native IPv6 communication*</br>

<u>Formatting</u></br>
\- 128 bits in an address (called a hextet)</br>
\- 8 sets of four hex values (separated by :)</br>
\- drop leading zeroes</br>
\- double colons should only happen once</br>
ex: 2001:0db8:0000:1111:0000:0000:0000:0200 → 2001:db8:0:1111::200</br>

<u>IPv6 Prefixes</u></br>
\- can be as many as /128</br>
\- reccomended to use a 64-bit interface id makes Stateless address autoconfig (SLAAC) and subnetting easier</br>

<u>IPv6 Casting</u></br>
Unicast: identifies 1 unique interface</br>
Multicast: 1 packet goes to multiple interface</br>
Anycast: 1 unicast address can be assigned to multiple devices</br>
\- an anycast packet is routed to the nearest device with the address</br>
*No broadcasting--can spam network*</br>

<u>Anycast</u></br>
\- load balancing</br>
\- go to the nearest server</br>

### Types of IPv6 Addresses ##

<u>Global Unique Addresses</u></br>
\- equivalent to an IPv4 public address</br>
\- required for internet access</br>
\- no NAT needed</br>

<u>Link-Local Addresses (LLA)</u></br>
\- traffic is one-hop</br>
\- local to a router</br>
\- routers can have multiple LLA (can be the same, somehow)</br>
\- fe80::/10 range</br>

<u>Unique Local Addresses</u></br>
*range c00::/7 to fdff::/7*</br>
\- similar to RFC 1918 private IPv4 addresses</br>
\- used for addressing within a site or group of sites</br>
\- can be used for devices that will never need to access another network</br>
\- not globally routed or translated to a global IPv4 address</br>
*many sites use RFC 1918 addresses as a security measure, which is not what ULAs were designed for*</br>

<u>IPv6 Global Unicast Addresses (GUAs)</u></br>
\- globally unique and routable on the IPv6 internet</br>
\- only start with 001 or 2000::/3</br>
\- begin with a decimal of 2 or 3</br>

### IPv6 Multicast ###

<u>Common Groups</u>
\- All-nodes group: all devices join</br>
\- All-routers: only routers (auto-joined with enabled with `ipv6 unicast-routing` global config command)</br>
**Multicast is the key to IPv6:** auto-joins "all nodes" and "all routers" groups</br>

<u>Solicited Node</u></br>
\- similar to all nodes</br>
\- mapped to special ethernet multicast address</br>
\- the ethernet NIC (network interface card) filters traffic by examining the dest mac address to see if the device is the intended target of the packet</br>
