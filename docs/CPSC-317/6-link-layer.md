# Link Layer

## Terms

- nodes
    - hosts and routers
- links
    - communication medium
    - wired links
    - wireless links
- frame
    - link layer packet
    - encapsulates datagram

- link layer is implemented in adapters, or Network Interface Cards (NIC)
- autonomous

two types of links
- point to point
    - dial-up
    - two routers
- broadcast
    - to every host on the network

## Link layer services

- framing (packetizing)
    - puts datagram into frame, adds header
    - broadcast
    - MAC, source and destination
- link access
    - MAC protocol
- reliable deliver (retransmission)
    - more often used on wireless links
- error detection and correction
    - caused by signal attenuation, noise

## Link layer frame (802.x)

Ethernet header: destination and source MAC addresses (6 bytes)

### MAC address

- 48 bits, or 6 bytes
- in hex
- allocation managed by IEEE, manufacturers buy portions of it
- portable, a device with a MAC address can move to a different IP

## Error detection and correction

EDC: error checking bit

### Single bit parity

Count the number of one's in data bits, 1 if odd, 0 if even

### 2D EDC

Do the bit parities for each row and each column. This can detect all but four parities in a square pattern

### Cyclic redundancy check (CRC)

- constants G and r
- r+1 is the length of G
- calculate remainder (modulo 2)
