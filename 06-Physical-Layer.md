# OSI 1: Physical Layer #

*Transports bits between network*
Last step in encapsulation: the bits are encoded and transmitted between devices
\- connection can be wired or wireless

<u>Standards</u>
\- ISO, IEEE, ANSI
\- Physical components, encoding, signaling
*NIC is a key component*

<u>Encoding</u>
\- predicatable patterns that can be interpreted
\- no voltage may be incorrectly interpreted as a string of zeroes
\- constrained by bandwidth

<u>Terminology</u>
Latency: data transfer time (including processing delays)
Throughput: measure of bits received over time (including overhead)
Goodput: measure of usable data received over time
*Goodput = Throughput - traffic overhead*

### Copper Cabling ###
10Mb/s - 40Gb/s

<u>Copper Cable</u>
\- most common: cheap and easy
\- low attenuation (weak over long time)
\- interference from EM, RF, and crosstalk
\- pay attention to cable length limits and use proper cable type
*coaxial, (un)shielded twisted pair*

<u>Unshielded Twisted Pair (UTP) Cable</u>
\- polarity cancels and the twisting changes to eliminate crosstalk
\- different categories (3, 5(e), 6(a), 7, 8) can carry better bandwidths

<u>Shielded Twisted Pair</u>
\- wires (and pairs of wires) have insulation to protect against crosstalk
\- better interference protection
\- more expensive
\- harder to install

<u>Coaxial Cable</u>
\- single large copper wire (well shielded)
\- woven copper braid or foil acts as a second wire and acts as a shield
\- usually used for internet and cable connections

<u>Crossover Cable</u>
*crossover vs straight-through doesn't matter as much--OS switches the pins programmatically*
\- host-to-host, switch-to-switch, router-to-router
\- pairs are switched

<u>Ethernet Straight Through</u>
\- Host to network
\- no pins are switched

<u>Rollover</u>
\- Console to router
\- Cisco proprietary
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
