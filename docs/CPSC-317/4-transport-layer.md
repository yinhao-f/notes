# Transport Layer

- logical communication between processes  
- multiplexing to different processes (ports)
    - think of delivering mail to the right person in a household
    - IP address gets you to the correct host, and port number gets you to the correct application on that host.  

## Segmentation

- TCP breaks messages into segments labeled with port numbers, and pass them to the network layer
- UDP segments are created in the application layer

## Stream vs packet

- TCP (reliable stream)
    - connection
    - ordered
    - flow and congestion control
    - slower, possible delays
- UDP (unreliable packet)
    - no connection
    - no order guarantee
    - no flow/congestion control
    - fast

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

## GBN and SR

### Go back N

- receiver window is just 1
    - if data received are out of order, discard them
    - only accept data in order, and move window forward
- sender + receiver window <= total window

### Selective repeat

- receiver window is usually the same as the sender window, and their sum <= total window
- only resend the packets that did not receive an ACK
    - no need to "go back" and resend all the following packets

## TCP

### Sequence numbers

Every byte has a sequence number, and the sequence number of a segment is that of the first byte. Only send ACK number of the last correctly received segment, even when the receiver can receive following segments in its window. 

### Connection establishment

#### Three-way handshake

- client sends SYN, specifies sequence number
- server sends SYN/ACK, confirms client's sequence number, specifies server's sequence number
- client sends ACK, confirms server's sequence number

Sequence numbers are randomized to avoid duplicates

### Connection termination

Both sides need to send a FIN and respond with an ACK
