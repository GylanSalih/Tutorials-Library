# Interfaces and Cables

RJ-45 - Registered Jack

**Ethernet**

Ethernet is a collection of network protocols / standards. Network protocols and standards are necessary to ensure there is a common mode of network communication between different devices.

**Bits**

Network speeds are measured in “**bits per second”** (bps). E.g., Kbps, Mbps, Gbps, etc. A bit is a value which can either be represented by a “0” or a “1”. When travelling over copper wire, this variation between a bit value of “1” and a bit value of “0” is determined by a fluctuation in the electric signal.

**Bytes**

A byte is a collection of 8 bits.

1 kilobit (Kb) - 1 000 bits

1 megabit (Mb) - 1 000 000 bits

1 gigabit (Gb) - 1 000 000 000 bits

1 terabit (Tb) - 1 000 000 000 000 bits

**Ethernet Standards**

These are all defined in the IEEE 802.3 standard in 1983. (IEEE - Institute of Electrical and Electronics Engineers)

| Speed | Common Name | IEEE Standard | Informal Name | Maximum Length |
| --- | --- | --- | --- | --- |
| 10 Mbps | Ethernet | 802.3i | 10 BASE-T | 100m |
| 100 Mbps | Fast Ethernet | 802.3u | 100 BASE-T | 100m |
| 1 Gbps | Gigabit Ethernet | 802.3ab | 100 BASE-T | 100m |
| 10 Gbps | 10 Gig Ethernet | 802.3an | 10G BASE-T | 100m |

BASE - Base Band Signaling

T - Twisted Pair

Copper cables used in ethernet standards are UTP Cables (Unshielded Twisted Pair). The twist help protect against EMI (Electro-Magnetic Interference).

4 Pairs - 8 Wires

10 BASE-T (Ethernet) and 100 BASE-T (Fast Ethernet) use two pairs of wires, while 100 BASE-T (Gigabit Ethernet) and 10G BASE-T (10Gig Ethernet) use all 4 pairs of wires. 

**10 BASE-T and 100 BASE-T**

- 10 BASE-T and 100 BASE-T make use of pin pairs 1 and 2, and 3 and 6.
- In 10 BASE-T and 100 BASE-T systems, PCs, Routers and Firewalls transmit data on pin pair 1 and 2 and receive data on pin pair 3 and 6.
- This is in contrast to Switches who receive data on pin pair 1 and 2, and transmit data on pin pair 3 and 6.
- The difference in pins allow for a full-duplex mode of communication. Meaning data can be transmitted and received at the same time.

**Straight-Through Cables**

These are used to transmit data between devices who transmit and receive data on different ports.

**Pin Connections in Straight-Through Cables:**

- 1 → 1
- 2 → 2
- 3 → 3
- 6 → 6

**Cross-Over Cables**

These are used to transmit data between network devices which transmit and receive data on the same pin pairs.

**Pin Connections in Straight-Through Cables:**

- 1 → 3
- 2 → 6
- 3 → 1
- 6 → 2

**Auto MDI-X**

This allows modern devices to detect the transmitting and receiving pins of the device they are connected to and then auto adjust the pins they use for transmitting and receiving data, allowing them to communicate with each other even if they are connected by a straight-through cable and share the same transmitting and receiving pin pairs.

**1000 BASE-T and 10G BASE-T**

- 1000 BASE-T and 10G BASE-T make use of 4 pin pairs of wires.
- Wires in 1000 BASE-T and 10G BASE-T are bidirectional, allowing data to be received and transmitted on any pin pair.

**Fiber Optic Cables and SFP Transceivers**

SFP - Small Form-Factor Pluggable

**Fiber Optic Cables**

These consist of two wires one used for transmitting data from each device and one used for receiving data from each device.

**Flow**

- Transmit → Receive
- Receive ← Transmit

**Structure of a Fiber Optic Cable (Inner-Most → Outer-Most)**

1. Fiberglass Core
2. Cladding that reflects light
3. Protective Buffer (Protects fiberglass from breaking)
4. Outer Jacket

**Types of Fiber Optic Cables**

- Multi-Mode
    - Core diameter is wider than single-mode fiber
    - Allows multiple angles of light to enter the fiberglass core
    - Allows longer cables than UTP, but shorter cables that single-mode fiber
    - Cheaper than single-mode fiber (Due to cheaper LED-based SFP transmitters)
    
- Single-Mode
    - Narrower than multi-mode fiber
    - Light enters at a single angle from a laser-based transmitter
    - Allows longer cables than both Multi-Mode and UTP cables
    - More expensive than multi-mode fiber due to more expensive laser based SFP Transmitter

| Informal Name | IEEE Standard | Speed | Cable Type | Maximum Cable Length |
| --- | --- | --- | --- | --- |
| 1000 BASE-LX | 802.3z | 1 Gbps | Multi-Mode Single-Mode | 550 m (MM)
5 km (SM) |
| 10G BASE-SR | 802.3ae | 10 Gbps | Multi-Mode | 400 m |
| 10G BASE-LR | 802.3ae | 10 Gbps | Single-Mode | 10 km |
| 10G BASE-ER | 802.3ae | 10 Gbps | Single-Mode | 30 km |