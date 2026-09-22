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
\- wires (and pairs of wires) have insulation to protect against crosstalk</br>
\- better interference protection</br>
\- more expensive</br>
\- harder to install</br>

<u>Coaxial Cable</u></br>
\- single large copper wire (well shielded)</br>
\- woven copper braid or foil acts as a second wire and acts as a shield</br>
\- usually used for internet and cable connections</br>

<u>Crossover Cable</u></br>
*crossover vs straight-through doesn't matter as much--OS switches the pins programmatically*</br>
\- host-to-host, switch-to-switch, router-to-router</br>
\- pairs are switched</br>

<u>Ethernet Straight Through</u></br>
\- Host to network</br>
\- no pins are switched</br>

<u>Rollover</u></br>
\- Console to router</br>
\- Cisco proprietary</br>
\- pins are inverted</br>

### Fiber Optic ###
10 Mb/s - 800 Gb/s</br>

<u>Fiber Optic</u></br>
\- light transmits across very clear glass</br>
\- no EMI or EFI</br>
\- some dispersion, but can transmit long-distance</br>
\- expensive, specialized</br>
\- encoded through laser or LED (laser is expensive)</br>

<u>Single Mode</u></br>
\- laser</br>
\- single beam (small core)</br>
\- long-distance</br>
\- typically yellow</br>

<u>Multimode</u></br>
\- LEDs</br>
\- larger core (light is transmitted at different angles)</br>
\- short distance</br>
\- typically orange</br>

<u>Suscriber Connector (SC)</u></br>
\- one-way only</br>
\- half-duplex</br>
\- identical (trial and error)</br>
*connector is not modal-specific*

### Wireless ###
2 Mb/s - 46 Gb/s</br>
\- coverage is dependent on physical environment</br>
\- susceptible to (un)intentional interference </br>
\- half-duplex: when multiple users access WLAN, all experience reduced bandwidth</br>
\- requires access point and NIC adapters</br>
