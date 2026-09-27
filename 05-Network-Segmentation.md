# Lecture 3: Network Segmentation

<u>Broadcasting Review</u>  
\- router is the last to receive a broadcast (does not propagate)  
\- broadcast address is when host bits are all ones

<u>Address Resolution Protocol (ARP)</u>  
\- used to locate other devices  
\- broadcasts a message to identify mac addresses from ip addresses (who is)  
\- excessive broadcasts can overrun a network

<u>Network bits cannot be changed</u>  
Ex: 10.0.0.0/8 $\rightarrow$ network is 10  
Ex: 10.0.0.0/16 $\rightarrow$ network is 10.0.0

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
\- use 10.0.0.0/16 as network segmentation (can use 10.0-255.0.0/16 as network segments)  
broadcast: 10.0.255.255 is subnet broadcast

<u>Magic Number</u>  
\- value of last bit of network prefix in subnet  
\- last octet of networks will be multiple of it

<u>Example: 192.168.1.0/27</u>  
first valid host: 192.168.1.1  
last valid host: 192.168.1.30  
broadcast: 192.168.1.31

<u>Example: 192.168.1.0/24</u>  
*want 2 hosts per subnetwork*  
\- 2 valid hosts + 2 invalid ips = 4 (2 bit)  
\- prefix of 30  
\- add 64 subnetworks  
\- subnet mask is 192.168.1.252

*Be able to identify the first valid host, last valid host, broadcast, and network*

<u>Variable Length Subnet Mask (VLSM)</u>  
*Subnetting a subnet*

![08fig40.jpg](images/08fig40.jpg)  
Academy, C., & Cisco Networking Academy Program,  author. (2013). Network Basics Companion Guide / Academy, Cisco. (1st edition). Cisco Press.
