# Lecture 3: Network Segmentation

<u>Broadcasting Review</u>  
\- router is the last to receive a broadcast (does not propagate)  
\- broadcast address is when host bits are all ones

<u>Address Resolution Protocol (ARP)</u>  
\- used to locate other devices  
\- broadcasts a message to identify mac addresses from ip addresses (who is)  
\- excessive broadcasts can overrun a network

<u>Network bits cannot be changed</u>  
Ex: 10.0.0.0/8 $\rightarrow$ network is 10 and host is 0.0.0  
Ex: 10.0.0.0/16 $\rightarrow$ network is 10.0.0 and host is 0

<u>Valid Hosts</u>  
\- $2^h - 2$ ($h =$ number of host bits)  
\- the 2 invalid host addresses are when the host bit are all zeroes or all ones (broadcast address)  
\- when host bits are all 0, it indicates the network as a whole--does not point to a host

<u>Number of Subnets</u>  
\- "borrow" from host bits  
\- $2^n =$ number of subnets ($n =$ number of "borrowed" bits)  
Ex: 192.168.1.0/24 $\rightarrow$ 192.168.1.0/26 = add 4 new networks

<u>Reasons for Segmentation</u>  
\- control security policies by network segment per user type  
\- reduces broadcast and overall network traffic (improve performance)

<u>Subnetting</u>  
/8  255.0.0.0  
/16 255.255.0.0  
/24 255.255.255.0

Example: 10.0.0.0/8  
\- use 10.0.0.0/16 as network segmentation  
 **Broadcast**: 10.0.255.255  
 **First host**: 10.0.0.1  
 **Last host**: 10.0.255.254

<u>Magic Number</u>  
\- value of last bit of network prefix in subnet  
\- last octet of networks will be multiple of it

<u>Example: 192.168.1.0/27</u>  
**Broadcast**: 192.168.1.31  
**First host**: 192.168.1.1  
**Last host**: 192.168.1.30

<u>Example: 192.168.1.0/24</u>  
*want 2 hosts per subnetwork*  
\- 2 valid hosts + 2 invalid IPs = 4 (2 bit)  
\- prefix of 30 (or /252)  
\- add 64 subnetworks  
\- subnet mask is 255.255.255.252  

<u>Variable Length Subnet Mask (VLSM)</u>  
*Subnetting a subnet*  
\- one (sub)network gets split into further subnets to better allocate IP space  
[This is a good resource](https://compsci.rocks/learn/networking/vlsm-practice/)  
![08fig40.jpg](images/08fig40.jpg)  
[^1]

[^1]: Academy, C., & Cisco Networking Academy Program,  author. (2013). Network Basics Companion Guide / Academy, Cisco. (1st edition). Cisco Press.