# Design of the Internet

Components:  
- hosts/end systems
- routers
- communication links
- local, regional networks

Multiplexing: data streams must share the medium

## Circuit switching

Analogous to telephone switching, dedicated path between source and destination

- multiple input streams share the path
- multiplexing: FDM and TDM
    - Frequency Division Multiplexing: divided by frequency bands
    - Time Division Multiplexing: divided into time slots
- pros:
    - guaranteed performance once connection established
    - no delay once connected
- cons:
    - poor utilization of traffic if it's bursty
    - connection set up time overhead
    - poor fault tolerance


## Packet switching

Data divided into packets to be sent, each can take different routes

Pros:  
- good statistical performance is enough
- bursty demand
- frequent new conversations
- better utilization of the medium

## Protocols

A protocol defines:  
- roles of communicating entities
- format of messages
- order of messages
- action taken on transmission of messages and other events

### Protocol stack

- application
- transport
- network
- link
- physical

Application, transport, and network layers are OS, link and physical are hardware

#### Application layer protocol

HTTP, email, DNS, FTP, etc.  
Think of the format of writing a letter

#### Transport layer protocol

TCP, UDP  
Handles hosts and ports  
Think of reliability of the postal service and making sure the mail reaches the right person  

#### Network layer protocol

IP Address  
Decides the best route to transport the message  
Think of a routing officer at a postal office or logistics center  

#### Link layer protocol

Ethernet  
Think of local delivery persons

#### Physical layer protocol

802.11g/b/n, 1000BASE-T  
Makes sure that the message is in the right format for the transport medium

