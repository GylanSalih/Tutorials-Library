# Switch Interfaces

Status Column - Layer 1

Protocol Column - Layer 2

`show ip interface brief`

- Unlike routers, switch interfaces are not in an administratively down state by default. This means that the interface’s state can change simple by being plugged in

`show interfaces status`

- Command “`show interfaces status`” can be used to gain more information regarding the status of the switch’s interfaces

- Duplex and Speed are auto by default on Cisco switches. This means it will negotiate with the connected device to select on a duplex mode and a speed

Command “`speed SPEED`” and “`duplex DUPLEX`” can be used to specify the speed and duplex of a switch interface

Command “`interface range INTERFACE-RANGE *'(f0/0 - 12)'*`” can be used to select a range of interfaces all at once. This command can be edited to “`interface range INTERFACE-RANGE, INTERFACE-RANGE '*(f0/0 - 5, f0/9 - 12)'*`”. This can be used to select specific interface ranges

*Switch interfaces that are not in use should be disabled with the shutdown command as them being enabled by default can be a security risk*

`Half Duplex`

- The device cannot send and receive data at the same time. If it is receiving a frame, it must wait before sending a frame

`Full Duplex`

- The device can send and receive data at the same time. It does not have to wait

**LAN Hubs**

- All devices attached to a hub must operate in half-duplex mode
- All devices connected to a hub are apart of a collision domain. This means that any packet that is sent can potentially collide with another packet, causing the information contained within both frames to be corrupted.
- To avoid this ethernet devices use a mechanism called CSMA/CD

**CSMA/CD - Carrier Sense Multiple Access with Collision Detection**

- Before sending frames devices listen to the collision domain until they detect that other devices are not sending
- If a collision still occurs, the device send a jamming signal to inform the other devices that a collision happened
- Each device will wait a random period of time before sending frames again
- The process repeats

`Speed /Duplex Auto Negotiation`

- Interfaces that can run at different speeds (10 / 100 or 10 / 100 / 1000) have default `speed auto` and `duplex auto`
- Interfaces “advertise” their capabilities to the neighboring device, and they negotiate the best speed and duplex settings they are both capable of
- If auto negotiation is turned off on the device that is connected to the switch’s interface, the interface will try to detect the devices speed. If this cannot be done, the interface will use its slowest supported speed
- If the speed is 10 or 100 Mbps, the switch will use half-duplex communication mode. If the speed is 1000 Mbps or greater, the interface will use full-duplex communication

**Interface Errors**

- Runts - Frames that are smaller than the minimum frame size (64 bytes)
- Giants - Frames that are larger than the maximum frame size (1518 bytes)
- CRC - Frames that failed the CRC check (In the ethernet FCS trailer)
- Frame - Frames that have an incorrect format (due to an error)
- Input Errors - Total of various counters, such as the above four
- Output Errors- Frames that switch tried to send, but failed due to an error