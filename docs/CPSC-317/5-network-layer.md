# Network Layer

## Readings

- 1.3.3, 5.intro, 5.3, 5.4
- 4.3, 4.3.1, 4.3.3 (before obtaining a host address), 4.3.5
- 4.3 (up to 4.3.2)
- 5.1, 5.2, 5.2.1, 5.2.2
- 5.4 (5.4.2)
- 4.3.4

## Learning goals

- how did "a network of networks" become ASes
- tiers of ASes
- relationship between ASes and organizations
- why addressses are assigned to interfaces instead of hosts
- define a network
- IP address forwarding
    - why network layer functions are divided into forwarding and routing
    - IPv4 format and meaning
    - classful vs. classless addressing (CIDR)
    - IPv4 vs. IPv6
    - header of network packet
    - header of IP protocol

## Autonomous systems

- first a few private networks
    - CAnet (now Canarie)
    - used by universities to share information
- turned into autonomous systems
    - has a range of IP addresses
    - needs to route its own addresses and those addresses outside

## Tiers of networks

Only a few tier 1 networks in the world. More at tier 2. The rest are tier 3. 

## Addresses (naming)

Addresses are used to identify interfaces. Interfaces are like WIFI and cellular data to phones. The connection needs to be established with a set interface. 

## Network

Two usages

1. a collection of computers and routers owned and administered by a single organization
2. a single shared communication medium connected to at least 2 interfaces

## IP

- delivers on best effort, no guarantees
- no state in routers
- forwarding
- routing

### Forwarding vs. routing

- forwarding
    - move a packet from the router's input to its output
    - data plane forwarding function
- routing
    - plan the route a packet takes to reach the destination
    - routing algorithms
    - control plane
        - Software-Defined Networking (SDN)

### IP header

- Internet Header Length (IHL): number of 32-bit words
    - IPv4 header is has IHL of 5, or 20 bytes
    - IPv6 has 8, or 40 bytes
- Time-to-Live (TTL) time limit for network to drop packet

### IP address

#### IPv4

4 one-byte numbers connected by dots. First and last addresses are never used for a host. The first (host number all 0's) address is used to represent the network and hosts that don't have an address yet. The last (host number all 1's) is used for broadcast, i.e. sending a datagram to all hosts. 

#### IPv4 original

8 bits for network, 24 bits for the host number within the network

#### IPv4 class based

- class A
    - prefix 0, network size 8 bits
- class B
    - 10 (128-191), 16 bits
- class C
    - 110 (192-223), 24 bits
- class D - multicast
    - 1110 (224-239), 32 bits
- class E (reserved)
    - 1111 (240-255), 32 bits

E.g. 192.168.10.52 is class C because 192 = 0b11000000


### Longest prefix matching
