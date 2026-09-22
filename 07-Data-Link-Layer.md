# OSI 2: Data Link Layer

<u>Data Link</u></br>
\- Transmits frames</br>
\- Encapsulates the network layer into frames</br>
\- Performs error detection on frames</br>

802 is the Ethernet standard (February 1980)</br>
![datalink-sublayers.png](images/datalink-sublayers.png)

**Logical Link Control (LLC)** $\rightarrow$ communicates between networking software (upper layers) and device hardware (lower layers)</br>
**Media Access Control (MAC)** $\rightarrow$ responsible for data encapsulation and media access control</br>

</u>Router Layer 2 Functions</u></br>
\- accepts a frame from the network medium</br>
\- de-encapsulates and parses the data</br>
\- re-encapsulates</br>
\- forwards it to appropriate next segment</br>

## Common WAN Topologies ##
<u>Point-to-point</u></br>
\- simplest and most common wan topology</br>
\- permanent link between two endpoints</br>

<u>Hub and Spoke</u></br>
\- interconnects branch sites through point-to-point links</br>
\- airline topology</br>

<u>Mesh</u></br>
\- high availability</br>
\- expensive interconnectivity</br>
\- number of connections between $n$ points $= \large \frac{n(n-1)}{2}$</br>

<u>Former Topologies</u></br>
\- Bus: systems chained together linearly and terminated at each end</br>
\- Ring: Bus but the two ends connect</br>

## Carrier Sense Multiple Access (CSMA) ##

Half duplex $\rightarrow$ only one device can send or receive at a time (WLAN and bus)</br>
Full duplex $\rightarrow$ transmit and receive on shared medium (Ethernet switches)</br>

<u>With Collision Detection (CSMA/CD)</u></br>
\- half duplex</br>
\- simultaneous transmission will emit collision signal</br>
\- devices detect collision</br>
\- devices wait a random period of time and retransmit</br>

<u>With Collision Avoidance (CSMA/CA)</u></br>
\- half duplex</br>
\- algorithm governs when a device can send</br>
\- during transmission, devices include a time duration needed for transmission</br>
\- other devices receive the time duration message and know when medium will be next available</br>

<u>Contention-Based Access</u></br>
\- all node operate in half-duplex</br>
\- compete for use of the medium</br>
\- CSMA/CD: bus-topology Ethernet</br>
\- CSMA/CA: WLANs</br>

<u>Controlled Access</u></br>
\- each node has its own time on the medium</br>
\- used on ARCNET and Token Ring</br>

## Datalink Frame ##
<u>Part 1: Header</u></br>
\- Frame Start: announces beginning of frame</br>
\- Addressing: source and dest nodes</br>
\- Type: identifies encapsulated Layer 3 protocol</br>
\- Control: identifies flow control services </br>

<u>Part 2: Data</u></br>
\- payload</br>

<u>Part 3: Trailer</u></br>
\- Error Detection: helps to determine transmission errors</br>
\- Frame Stop: announces end of frame</br>