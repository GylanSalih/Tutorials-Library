# IPv4 Addressing (Part 2)

Maximum hosts per network = 2^(Rest Bits / Host portion) - 2. E.g.,:

- **192.168.1.0/24**
    - 192.168.1.0 → 192.168.1.255 = 256 Addresses
    - Address where host portion is all 0s is the network address (192.168.1.0) and address where the host portion is all 1s is the broadcast address (192.168.1.255). i.e., Total usable host address apart of the 192.168.1.0/24 network is:
        - 256 - (1 (Network Address) + 1 (Broadcast Address) = 254 Addresses
        
- **172.16.0.0/16**
    - 2^16 = 65 536 Address
        - 65 536 - 2 = 65 534 Usable Addresses

Command “`show ip interface brief`” can be used to get info on the devices interfaces

- Status Column - The Layer 1 status of the interface
    - Administratively Down
        - Router interfaces default state - Interface has been disabled with the “`shutdown`” command
        - Switch interfaces are **NOT** administratively down by default
- Protocol Column - The Layer 2 status of the interface

**Commands**

- Command “`interface INTERFACE-NAME`” can be used to configure an interface

- Command “`ip address IP-ADDRESS NETMASK`“ can be used to configure an IP Address on a specific interface

- Command “`no shutdown`” can be used to change the interfaces Status field from administratively down, which is its default state

- Command “`show interfaces INTERFACE-ID`” can be used to show information about a certain interface

- Command “`description DESCRIPTION`” can be used to configure a description on the interfaces

- Command “`show interfaces description`” can be used to see the interfaces configured description