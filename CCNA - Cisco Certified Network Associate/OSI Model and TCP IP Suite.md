# OSI Model and TCP/IP Suite

**Networking Models**

Networking Models categorize and provide a structure for networking protocols and standards. (Networking Protocol - A set of rules defining how network devices and software should work {Logical Rules} ).

Alt - A set of guidelines and standards that define how data is transmitted and received over a network. Networking Models provide a common framework for network devices and software to communicate with each other

**OSI Model - Open Systems Interconnection Model**

- Open - It is an open standard, meaning, it is not a standard used by any single company.
- It is a conceptual model that categorizes and standardizes the different function in a network.
- Created by the ‘International Organization for Standardization’ (ISO)
- Functions are divided into 7  “Layers”.

| 7 | Application | - Closest to the end user
- Interacts with software application protocols
- HTTP and HTTPS are examples of Layer 7 protocols | - Identifying communication partners
- Synchronizing communication |
| --- | --- | --- | --- |
| 6 | Presentation | - Data in the application layer is in an “application” format
- It is the job of the presentation layer to translate this data into a network format
- It is also responsible for the Encryption and Decryption of data |  |
| 5 | Session | - Controls dialogs between communication hosts
- Establishes. manages and terminates connections between the local application (E.g., Web Browser) and the remote application (E.g., YouTube) |  |
| 4 | Transport | - Segments and reassembles data for communication between end hosts
- Breaks large pieces of data into smaller segments which can be more easily sent over the network
- Provides **host-host** communication / **end-end** communication / **process-to-process** communication for applications | - Adds a layer 4 header to data
- At his point the data is referred to as a segment
- If data is large enough it will be segmented and a layer 4 header will be added to each segment |
| 3 | Network | - Provides connectivity between end hosts on different networks
- Provides logical addressing (IP Address)
- Provides data path selection
- Routers operate at layer 3 | - Adds a layer 3 header
- At this point the encapsulated data is called a packet |
| 2 | Data Link | - Provides **node-to-node** connectivity and data transfers
- Defines how data is formatted for transmission over a physical medium (E.g., Copper UTP Cables)
- Detects and possibly corrects Physical Layer errors
- Uses Layer 2 addressing, separate from Layer3 addressing (MAC Address - Media Access Control Address)
- Switches operate at Layer 2 | - Adds on a layer 2 header and trailer
- At this point the encapsulated data is referred to as a frame |
| 1 | Physical | - Defines physical characteristics of the medium used to transfer data between devices (Voltage Levels, Max Transmission Distance, etc)
- Digital bits are converted to electrical (for wired connections) or radio (for wireless connections) signals. | - Data is referred to as a bit |

PDU - Protocol Data Unit (Segment, Packet, Frame and Bit)

**Adjacent Layer Interactions**

These are interaction between different layers within the same OSI stack on the same device.

**Same Layer Interactions**

These are interactions between the same layer from separate OSI stacks / different devices.

**TCP/IP Suite**

- Conceptual model and set of communications protocols used in the internet and other networks
- Known as TCP/IP because those are two foundational  protocols in the suite
- Developed by the United States Department of Defense through DARPA (Defense Advanced Research Agency)
- Similar structure to the OSI Model, but with fewer layers
- The TCP/IP Model is the network model actually in use today
    
    
    | 4 | Application | Application
    Presentation
    Session |
    | --- | --- | --- |
    | 3 | Transport | Transport |
    | 2 | Internet | Network |
    | 1 | Link | Data Link
    Physical |