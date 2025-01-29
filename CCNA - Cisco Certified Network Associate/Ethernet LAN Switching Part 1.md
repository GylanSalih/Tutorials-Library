# Ethernet LAN Switching Part 1

Local Area Network (LAN)

A network contained within a relatively small area. Routers are used to connect different LANs together. Devices connected to the router on different interfaces are apart of separate LANs.

Ethernet Frame

- Header
    - Preamble
    - SFD - Start Frame Delimiter
    - Destination
    - Source
    - Type
- Trailer
    - FCS - Frame Check Sequence
    

Preamble

- 7 bytes long (56 bits)
- Alternating 1s and 0s (10101010 * 7)
- Allows devices to synchronize their receiver clocks

SFD - Start Frame Delimiter

- 1 byte long (8 bits)
- 10101011
- Marks the end of the Preamble and the beginning of the rest of the frame

Destination and Source

- Indicates the devices sending and receiving the frame
- Consists of the destination and source ‘MAC Address’
- MAC - Media Access Control
- 6 bytes lone (48 bits)
- Sometimes referred to as the device’s “Burnt in Address”

Type OR Field

- 2 bytes long (16 bits)
- If value is 1500 or less, this indicates the LENGTH of the encapsulated packet
- If value is 1536 or greater, this indicates the TYPE of the encapsulated packet (usually IPv4 or IPv6)
    - IPv4 - 0x0800 (2048 in decimal)
    - IPv6 -  0x86DD (34525 in decimal)

FCS - Frame Check Sequence

- 4 bytes long (32 bits)
- Detects corrupt data by running a “CRC” algorithm over the received data
- CRC - Cyclic Redundancy Check

Full length of Ethernet header and trailer is **26 bytes**

MAC Addresses

- 6 bytes long (48 bits)
- Assigned to the device when it is made
- AKA. “Burned-In Address” (BIA)
- Is globally unique
- First 3 bytes are the OUI (Organizationally Unique Identifier), which is assigned to the company making the device
- Last 3 bytes are unique to the device itself
- Written as 12 hexadecimal characters

Unicast Frame

- A frame destined for a single target

Dynamically Learned MAC Address

- A MAC Address which was not manually configured within a devices MAC Address table, but was instead dynamically learnt
- They are removed from a devices MAC Address table after 5 minutes of inactivity

A switch’s MAC Address Table will be populated using the source address marked on any of the frames sent to it

Unknown Unicast Frame

- A frame for which a switch does not have a known MAC Address entry within its MAC Address table
- This type of frame will be flooded through all of the switch’s interfaces, except the one which it received the frame from

Known Unicast Frame

- A frame for which a switch knows the interface which connects to the frame’s destination address
- This type of frame is not flooded but are instead forwarded directly to the destination