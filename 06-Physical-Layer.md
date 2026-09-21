# OSI 1: Physical Layer #

*Transports bits between network*</br>
Last step in encapsulation: the bits are encoded and transmitted between devices</br>
\- connection can be wired or wireless</br>

<u>Standards</u></br>
\- ISO, IEEE, ANSI</br>
\- Physical components, encoding, signaling</br>
*NIC is a key component*</br>

<u>Encoding</u></br>
\- predicatable patterns that can be interpreted</br>
\- no voltage may be incorrectly interpreted as a string of zeroes</br>
\- constrained by bandwidth</br>

<u>Terminology</u></br>
Latency: data transfer time (including processing delays)</br>
Throughput: measure of bits received over time (including overhead)</br>
Goodput: measure of usable data received over time</br>
*Goodput = Throughput - traffic overhead*</br>

### Copper Cabling ###
10Mb/s - 40Gb/s</br>

<u>Copper Cable</u></br>
\- most common: cheap and easy</br>
\- low attenuation (weak over long time)</br>
\- interference from EM, RF, and crosstalk</br>
\- pay attention to cable length limits and use proper cable type</br>
*coaxial, (un)shielded twisted pair*</br>

<u>Unshielded Twisted Pair (UTP) Cable</u></br>
\- polarity cancels and the twisting changes to eliminate crosstalk</br>
\- different categories (3, 5(e), 6(a), 7, 8) can carry better bandwidths</br>

<u>Shielded Twisted Pair</u></br>
\- wires (and pairs of wires) have insulation to protect against crosstalk
\- better interference protection
\- more expensive
\- harder to install

<u>Coaxial Cable</u>
\- single large copper wire (well shielded)
\- woven copper braid or foil acts as a second wire and and as a shield
\- usually used for internet and cable connections

<u>Crossover Cable</u></br>
*crossover vs straight-through doesn't matter as much--OS switches the pins programmatically*</br>
\- host-to-host, switch-to-switch, router-to-router</br>
\- pairs are switched</br>

<u>Ethernet Straight Through</u></br>
\- Host to network</br>
\- no pins are switched

<u>Rollover</u></br>
\- Console to router</br>
\- Cisco proprietary</br>
\- pins are inverted

### Fiber Optic ###
10 Mb/s - 800 Gb/s

<u>Fiber Optic</u>
\- light transmits across very clear glass
\- no EMI or EFI
\- some dispersion, but can transmit long-distance
\- expensive, specialized
\- encoded through laser or LED (laser is expensive)

<u>Single Mode</u>
\- laser
\- single beam (small core)
\- long-distance
\- typically yellow

<u>Multimode</u>
\- LEDs
\- larger core (light is transmitted at different angles)
\- short distance
\- typically orange

<u>Suscriber Connector (SC)</u>
\- one-way only
\- half-duplex
\- identical (trial and error)
*connector is not modal-specific*

### Wireless ###
2 Mb/s - 46 Gb/s
\- coverage is dependent on physical environment
\- susceptible to (un)intentional interference 
\- half-duplex: when multiple users access WLAN, all experience reduced bandwidth
\- requires access point and NIC adapters
