# Transport Layer

Provide logical communication between processes  
IP address gets you to the correct host, and port number gets you to the correct application on that host.  

## Segmentation

Transport layer breaks messages into segments labeled with port numbers, and pass them to the network layer. For UDP, segments are created in the application layer.  

TCP offers flow control and congestion control  

## Checksum

Some function to compute on the data, e.g. 1's complement. Receiver runs the same function, check if results match. If one bit is changed, we can detect the error. If two bits are changed, it's not guaranteed. 

## UDP Socket in Java

`DatagramPacket`

## Protocol and state machines

The protocol can be defined by a finite state machine

## Reliable data transfer

In the transport layer, we assume that there is a reliable data channel. But this is actually an abstraction of the unreliable channel in the network layer. 

### Reliable service implementation

`rdt_send()`, `udt_send()`  
`rdt_rcv()`, `deliver_data()`  

Sender sends the message with a checksum, receiver checks the data and sends a ACK/NAK back to the sender. But if the ACK/NAK is corrupted, what should the sender do? If the sender:

- ignores the corrupt ACK/NAK: both gets stuck, sender waiting for ACK/NAK and receiver waiting for data
- treat as ACK: if it's NAK, the receiver never gets the data
- treat as NAK: if it's ACK, the receiver gets duplicate data


