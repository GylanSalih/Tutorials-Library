# IPv4 Addressing (Part 1)

**Source IP Address and Destination IP Address**

- 32 bits (4 bytes) long (each)
- A series of 32 binary bits split up into 4 octets (8 bits each) then written in dotted decimal format to make it easily read
- /8 /16 /24 /32 - These represent the network portion of the IP Address
    - /8 - First Octet
    - /16 - First two octets
    - /24 - First three octets
    - /32 - All four octets

**IPv4 Address Classes**

| Class | First Octet | First Octet Numeric Range | Prefix Length | Netmask |  |
| --- | --- | --- | --- | --- | --- |
| A | 0xxxxxxx | 0 - 127 | /8 | 255.0.0.0 | - 127 Range is reserved for loopback addresses

- Used to test the network stack |
| B | 10xxxxxx | 128 - 191 | /16 | 255.255.0.0 |  |
| C | 110xxxxx | 192 - 223 | /24 | 255.255.255.0 |  |
| D | 1110xxxx | 224 - 239 |  |  | - Multicast Addresses |
| E | 1111xxxx | 240 - 255 |  |  | - Reserved (Experimental Purposes) |

**Network Address**

- If the host portion of the address is all 0s then it is the network address
- Cannot be assigned to a host

**Broadcast Address**

- If the host portion of the address is all 1s, then it is the broadcast address
- Cannot be assigned to a host