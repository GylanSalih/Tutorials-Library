# The IPv4 Header

Minimum IPv4 Header Length - 20 bytes (Indicated by a value of 5 in the IHL field)

Maximum IPv4 Header Length - 60 bytes (Indicated by a value of 15 in the IHL field)

**Version**

- 4 bits long
- Identifies the version of IP used
    - IPv4 - 0100
    - IPv6 - 0110

**IHL - Internet Header Length**

- 4 bits long
- The final field of the IPv4 header (Options) is variable in length, so this is necessary to indicate the total length pf the header
- Indicates the length of the header in 4-byte increments (E.g., A value of 5 would indicate a header size of 5 * 4 = 20 bytes)
    - Minimum Value - 5 (5 * 4 = 20 bytes)
    - Maximum Value - 15 (15 * 4 = 60 bytes)

**DSCP - Differentiated Services Code Point**

- 6 bits long
- Used for QoS (Quality of Service)
- Used to priorities delay-sensitive data (streaming voice, video, etc.)

**ECN - Explicit Congestion Notification**

- 2 bits long
- Provides end-to-end (between two endpoints) notification of the network congestion without dropping packets)
- Optional feature that requires both endpoints, as well as the underlying network infrastructure, to support it

**Total Length Field**

- 16 bits long
- Indicates the total length of the packet (L3 Header + L4 Segment)
- Measured in bytes (not 4 byte increments in the IHL)
- Minimum value of 20 (IPv4 Header with no encapsulated data)
- Maximum value of 65535 (Maximum 16 bit value)

**Identification Field**

- 16 bits long
- If a packet is fragmented dur to being too large, this field is used to identify which packet the fragment belongs to
- All fragments of the same packet will have their own IPv4 header with the same value in this field
- Packets are fragmented if larger than the MTU (Maximum Transmission Unit)
- MTU is usually 1500 bytes
- Fragments are reassembled by the receiving host

**Flags**

- 3 bits long
- Used to control / Identify fragments
- Bit 0 - Reserved, always set to 0
- Bit 1 - Don’t Fragment (DF Bit), used to indicate a packet that should not be fragmented
- Bit 2 - More fragments (MF Bit), set to 1 if there are more fragments in the packet, set to 0 for the last fragment
    - If the packet is a unfragmented packet, the MF Bit will automatically be set to 0

**Fragment Offset Field**

- 13 bits long
- Used to indicate the position of the fragment within the original, unfragmented IP packet
- Allows fragment packets to be reassembled even if the fragment arrives out of order

**Time To Live Field**

- 8 bits length
- A router will drop a packet with a TTL of 0
- Used to prevent infinite loops
- Originally designed to indicate the packet’s maximum lifetime in second
- In practice, indicates a “hop count” - Each time the packet arrives at a router, the router decreases the TTL by 1
- Recommended default TTL is 64

**Protocol**

- 8 bits long
- Indicates the protocol of the encapsulated L4PDU
    - Value of 6 - TCP
    - Value of 17 - UDP
    - Value of 1 - ICMP
    - Value of 89 - OSPF (dynamic routing protocol)
    

**Header Checksum Field**

- 16 bits long
- A calculated checksum used to check for errors in the IPv4 header
- When a router receives a packet, it calculates the checksum of the header and compares it to the one in this field of the header
- If they do not match, the router drops the packet
- Used to check for the errors only in the IPv4 header
- IP relies in the encapsulated protocol to detect errors in the encapsulated data
- Both TCP and UDP have their own checksum fields to detect errors in the encapsulated data

**Source / Destination IP Address Field**

- 32 bits long
- Source IP Address - IPv4 Address of the sender of the packet
- Destination IP Address - IPv4 Address of the intended receiver of the packet

**Options**

- Can be 0 - 320 bits in length
- Rarely used
- If the IHL field is greater than 5, it means that options are present