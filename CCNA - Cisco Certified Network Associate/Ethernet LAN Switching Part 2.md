# Ethernet LAN Switching Part 2

Broadcast MAC Address - FFFF.FFFF.FFFF

**Ethernet Frame**

- The Preamble and SFD are sometimes not considered to be apart of the ethernet header. This mean the total size of the ethernet header + trailer is 18 bytes
- The minimum size for an ethernet frame (Header + Payload + Trailer) is 64 bytes. 64 bytes - 18 bytes = 46 bytes. i.e., The minimum payload size is 46 bytes.
- The maximum size of an ethernet frame payload is 1500 bytes
- If the payload is less that 46 bytes then padding bytes are added (These bytes consist of all zeros).

**ARP - Address Resolution Protocol**

- ARP is used to discover the Layer 2 address (MAC Address) of a known Layer 3 address (IP Address)
- Consists of two messages. ARP Request and ARP Reply
- The ARP Request is sent as a broadcast message. This means it is sent to all hosts on the network
- The ARP Reply is sent as a Unicast message
- ARP - 0x0806

**ARP Table**

- Command “`arp -a`” can be used to view a devices ARP Table. Cisco IOS command to view ARP Table is “`show arp`”
- Internet Address Column - IP Address (Layer 3)
- Physical Address Column - MAC Address (Layer 2)
- Type:
    - Static - Default Entry
    - Dynamic - Learned via ARP

**Ping**

- A network utility that is used to test reachability
- Measures round-trip time
- Uses two messages:
    - ICMP Echo Request
    - ICMP Echo Reply
- Command “`ping IP-ADDRESS size SIZE`” can be used to send a ping of a certain size

**MAC Address Table**

- Command “show mac address-table” can be used to view a switches MAC Address Table
- Aging is the process by which dynamic MAC Addresses are automatically removed from the MAC Address Table
- Command “`clear mac address-table dynamic`” can be used to clear all dynamic MAC Addresses from the  MAC Address Table
- The previous command can further be edited to “`clear mac address-table dynamic address MAC-ADDRESS`”. This command will clear the dynamic address within the MAC Address table which matches the one which was entered
- Again, this command can be edited to “`clear mac address-table dynamic interface INTERFACE`”. This command will clear any dynamic MAC Address which is linked to the interface which was entered