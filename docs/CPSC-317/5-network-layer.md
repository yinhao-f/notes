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
    - IP address and forwarding in routers
    - longest prefix matching
    - non-routable IP address
    - how organizations get IPs
    - IP subdividing and aggregation
    - given a router, a forwarding table, and a packet, decide which link to forward to
    - trace a packet given some routers, forwarding tables, and a packet
- intra-domain routing
    - why different routing algorithms are used within and between ASes
    - what is link state routing
    - Dijkstra's algorithm on a routing graph
    - what is distance vector routing
    - execute distance vector routing
    - compare link state and distance vector
- inter-domain routing
    - how routing decisions are made in the view of AS
    - what are iBGP, eBGP, peering, transit, and border
    - types of information exchanged by eBGP
    - given multiple routes to a destination, what are the factors in the decision of routing
    - using hot potato routing, how is a packet forwarded to another AS
    - issues with BGP and mitigations
- software-defined networking
    - where control plane is run in SDN

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

Addresses are used to identify interfaces. Interface sits between the host or the router and the physical link when sending an IP datagram. 

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
    - actual bits for use are 7
- class B
    - 10 (128-191), 16 bits
    - actual bits available are 14
- class C
    - 110 (192-223), 24 bits
- class D - multicast
    - 1110 (224-239), 32 bits
- class E (reserved)
    - 1111 (240-255), 32 bits

E.g. 192.168.10.52 is class C because 192 = 0b11000000

#### IPv4 classless (CIDR)

- IP address with a `/` and a number indicating the number of network bits
- routers only care about the network address, which is by setting the host bits to zero
    - this is also called the netmask (e.g. 255.255.255.0)
- **when calculating the number of hosts, remember to subtract 2** (addresses that are all 0's and all 1's)

#### IPv6

- 128 bits, 32 hexits, 4 hexits a group separated by colons
    - e.g. ABCD:ABCD:ABCD...
- network (48 bits) + subnet (16 bits) + host (64 bits)
- zeroes can be omitted

### Forwarding

- decide if an IP is in the same network
    - that way we don't need to send it through the router
    - compare the network address bits and see if they match
- each router keeps a forwarding table that matches destination IP range to the link
    - formally Forwarding Information Base (FIB)
    - built from aggregating information from other routers

#### Longest prefix matching

if more than one range matches in the forwarding table, the most specific is used

#### Non-routable address

- 10.0.0.0/8
- 172.16.0.0/12
- 192.168.0.0/16

### IP address assignment

- Regional Internet Registries assign to ISPs
- ISPs assign to customer ISPs
- IRL this can be messy as addresses run out

### Address range aggregation

- useful when collapsing address range information, e.g. advertising network ranges
- ranges can be aggregated if
    - all ranges combined are covered
    - new range doesn't contain groups not covered
    - e.g. 01 and 10 cannot be aggregated, but 0x and 01 can

### Address range division

- divide a range into smaller ranges
- set the first unfixed bit as a fixed bit
    - one group has bit 0, the other has 1

### Routing

- static
    - configured by network operators
- dynamic
    - routing protocol
    - distributed and decentralized
    - routers share information
- software (SDN)

#### Interior Gateway Protocols (IGP)

- routing within an AS
- small scale, limited

##### Link state

- broadcast link information to all routers
- make a map of the network
- uses Dijkstra's algorithm to find the shortest paths and updates forwarding table

##### Distance vector

- send local information to neighboring routers
- make signposts for routing
- if there's a shorter path through a router, update to route through this router
- assuming no link change cost, it takes the diameter of the graph many iterations for the routes to converge
    - diameter of graph?
- forwarding loop
    - happens if the link cost increases
    - can be mitigated by poisoned reverse, but only for loops involving two nodes

##### LS vs DV

$N=$ number of nodes, $L=$ number of links

- communication cost
    - LS: $O(N^2)$ because of number of messages to send
    - DV: diameter of the graph
- routing update cost while the algorithm is converging. DV also suffers
from the count-to-infinity problem
    - LS: $O(N^2)$ for adjacency matrix and linear search, $O(L + N \log N)$ for adjacency list of edges and using Fibonacci heap
    - DV: slower, can suffer from routing loops and count to infinity
- robustness
    - LS: more resilient to failures and packet loss during broadcasts
    - DV: misinformation can be spread widely; real world example of this

##### Routing algorithms

- Open Shortest Path First (OSPF)
    - most used IGP
    - link state
- Intermediate System to Intermediate System (IS-IS)
    - intermediate system = router
    - popular for large ISPs
    - link state
    - use link layer frames rather than IP
- Enhanced Interior Gateway Routing Protocol (EIGRP)
    - Cisco standard
    - distance vector
    - fast converge time
- Routing Information Protocol (RIP)
    - original distance vector
    - slow converge time

#### Exterior Gateway Protocols (EGP)

- peering
    - two ISPs passing traffic to each other for their customers
- transit
    - passing traffic across an AS to a different AS
- stub ASes
    - have a single or two providers as their Internet Gateway
    - no reason for a transit traffic to go through a stub AS
        - stub = end of something
- AS's view
    - appear as a single entity to other ASes
    - presents what networks are reachable from it
- internal routers
    - route traffic in its own network (IGP)
- border routers
    - route traffic at the edge of ASes
- edge routers
    - connect a home or company network to the rest of AS

##### Border Gateway Protocol (BGP)

- executed by border routers
- forms backbones of the internet with IP
- uses aggregation or summarization between ASes to reduce table sizes
    - also called supernet inside an AS
- eBGP
    - obtain subnet reachability information from neighboring ASes
    - path vector routing
        - advertise prefix, AS number + AS path + next hop
        - receiver builds forwarding table based on rules
- iBGP
    - broadcast reachability information to all internal routers
- hot potato routing
    - hand the packet to another AS as soon as possible
- BGP route hijacking
    - advertise a prefix as a false AS
    - can cause re-routing and DOS
    - mitigations
        - transit AS filter false advertisement
        - tedious

#### SDN

- intra-AS routing
- centralized decision, better than distributed
