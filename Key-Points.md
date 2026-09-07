
## Router Config ##
<u>Passwords</u></br>
`# enable password` protects console access</br>
`# enable secret password` protects privileged EXEC mode</br>
`# service password-encryption` encrypts passwords</br>

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

## Important to memorize ##

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
