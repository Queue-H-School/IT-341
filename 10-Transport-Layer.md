# OSI 4: Transport Layer 
\- segmenting and reassembling data</br>
\- adds leader info</br>
\- manage conversations</br>

## Transmission Control Protocol (TCP)
<u>Connection Oriented</u></br>
\- sequencing, acknowledgement, retransmission</br>
\- flow rate control</br>
\- TCP three-way handshake</br>

<u>TCP Header</u></br>
\- 20 bytes</br>
![tcp-header.png](images/tcp-header.png)</br>
\- source and destination port</br>
\- sequence number $\rightarrow$ packet number</br>
\- acknowledgement number $\rightarrow$ what to expect next</br>
\- window size $\rightarrow$ flow control</br>
\- control bits $\rightarrow$ TCP flag </br>

<u>Three Way Handshake</u></br>
![3-way-handshake-init.png](images/3-way-handshake-init.png)
1. client initiates client-to-server session with the server (SYN, SEQ)</br>
2. the server acknowledge session and requests server-to-client session (SEQ, ACK, CTL=SYN, ACK)</br>
3. client acknowledges server to client session (SEQ, ACK, CTL=ACK)</br>

<u>Half Open Window</u></br>
\- DDOS attack (opens multiple ports and sucks up memory)</br>
\- set time and rate limits to prevent predicatable DDOS patterns</br>

<u>Session Termination</u></br>
1. client sends FIN</br>
2. server sends ACK and FIN</br>
3. client sends ACK</br>

CTL $\rightarrow$ control fields</br>
URG $\rightarrow$ indicates priority</br>
ACK $\rightarrow$ acknowledgement number (packet received)</br>
PSH $\rightarrow$ request immediate data delivery to receiving host, without waiting for buffering</br>
RST $\rightarrow$ reset (terminate session immediately without fin-ack process)</br>
SYN $\rightarrow$ sequence number (packet sent)</br>
FIN $\rightarrow$ connection termination</br>
CHK $\rightarrow$ checksum</br>
SEQ $\rightarrow$ sequence number</br>

<u>(Old) ACK</u></br>
\- only represented the last packet received before packet loss</br>
\- client would have to re-send all post-ack packets, even if some had been received successfully</br>

<u>SACK</u></br>
\- if both hosts support SACK, reduces redundant retransmission</br>
\- Selective acknowledgement allows for the retransmission of *just* the dropped packet(s)</br>

<u>Maximum Segment Size (MSS)</u></br>
At Layer 2: TCP and IPv4 headers reduce MSS to 1460</br>
\- even if a device can receive more at Layer 3, it is still hindered by the Layer 2 MSS</br>

<u>Congestion Avoidance</u></br>
\- retransmissions due to congestion can exacerbate congestion</br>
\- different algorithms</br>

## User Datagram Protocol (UDP)
<u>Connectionless</u></br>
\- best-effort</br>
\- no reliability or acknowledgement</br>
\- little overhead or checking</br>

<u>UDP Header</u></br>
\- 8 bytes</br>
![udp-header.png](images/udp-header.png)
\- source and dest ports
\- length $\rightarrow$ length of the header

## Port Numbers ##
![socket-pairs.png](images/socket-pairs.png)
<u>Socket Pairs</u></br>
\- source port number is randomly generated bc it doesn't matter</br>
\- dest port matches application protocol</br>
*IP + port = socket*</br>
\- sockets are unique (hosts will not generate a duplicate source port)</br>
\- sockets allow for multiple processes on the same client or host to distinguish themselves</br>

![well-known-ports.jpg](images/well-known-ports.jpg)
only one application can be listening on a port at a time




