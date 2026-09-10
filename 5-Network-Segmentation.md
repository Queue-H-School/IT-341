# Lecture 3: Network Segmentation

<u>Broadcasting Review</u></br>
\- router is the last to receive a broadcast (does not propagate)</br>
\- broadcast address is when host bits are all ones

<u>Address Resolution Protocol (ARP)</u></br>
\- used to locate other devices</br>
\- broadcasts a message to identify mac addresses from ip addresses (who is)</br>
\- excessive broadcasts can overrun a network</br>

<u>Network bits cannot be changed</u></br>
Ex: 10.0.0.0/8 $\rightarrow$ network is 10</br>
Ex: 10.0.0.0/16 $\rightarrow$ network is 10.0.0</br>

<u>Valid Hosts</u></br>
\- $2^h - 2$ ($h =$ number of host bits)</br>
\- the 2 invalid host addresses are when the host bit are all zeroes or all ones (broadcast address)</br>
\- when host bits are all 0, it indicates the network as a whole--does not point to a host</br>

<u>Number of Subnets</u></br>
\- "borrow" from host bits</br>
\- $2^n =$ number of subnets ($n =$ number of "borrowed" bits)</br>
Ex: 192.168.1.0/24 $\rightarrow$ 192.168.1.0/26 = add 4 new networks</br>

<u>Reasons for Segmentation</u></br>
\- control security policies by network segment per user type</br>
\- reduces broadcast and overall network traffic (improve performance)</br>

<u>Subnetting</u></br>
/8  255.0.0.0</br>
/16 255.255.0.0</br>
/24 255.255.255.0</br>

Example: 10.0.0.0/8</br>
\- use 10.0.0.0/16 as network segmentation (can use 10.0-255.0.0/16 as network segments)</br>
broadcast: 10.0.255.255 is subnet broadcast</br>

<u>Magic Number</u></br>
\- value of last bit of network prefix in subnet</br>
\- last octet of networks will be multiple of it</br>

<u>Example: 192.168.1.0/27</u></br>
first valid host: 192.168.1.1</br>
last valid host: 192.168.1.30</br>
broadcast: 192.168.1.31</br>

<u>Example: 192.168.1.0/24</u></br>
*want 2 hosts per subnetwork*</br>
\- 2 valid hosts + 2 invalid ips = 4 (2 bit)</br>
\- prefix of 30</br>
\- add 64 subnetworks</br>
\- subnet mask is 192.168.1.252</br>

*Be able to identify the first valid host, last valid host, broadcast, and network*</br>

<u>Variable Length Subnet Mask (VLSM)</u></br>
*Subnetting a subnet*</br>

![08fig40.jpg](08fig40.jpg)
Academy, C., & Cisco Networking Academy Program,  author. (2013). Network Basics Companion Guide / Academy, Cisco. (1st edition). Cisco Press.
