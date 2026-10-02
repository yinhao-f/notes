# Application Layer

## Design for application layer protocols

- each application will define its own protocol
- open vs proprietary
- client-server, peer-to-peer
- choice of transport protocol
- types and formats of messages

## Open and proprietary protocols

### Open

- DICT, HTTP, SMTP, SSH
- usually defined in RFCs
- many different implementations

### Proprietary

- Skype, Zoom
- only one implementation

## Client-server architecture

- well defined roles
- server always on
- client establishes connection
- always between one client and one server

## Peer-to-peer architecture

- usually between peers with the same hierarchical role
- peers request service from other peers, provide service in return
- self scalability
- complex peer address management

## Quality of service

- data loss
- time sensitivity
- bandwidth

### UDP

- simple, fast
- unreliable, no order guarantee

### TCP

- reliable, order guarantee, congestion control
- slower

### Examples

- file transfer, web, email $\rightarrow$ TCP
- media streaming $\rightarrow$ UDP
- DNS $\rightarrow$ UDP

## Transport layer address and socket

### Transport layer address

Host name plus a port number

### Socket

Network endpoint created using system call `socket()`  
`close()`, `send()` or `write()`, `recv()` or `read()`, `close()`

## HTTP

- the World Wide Web's main application layer protocol
- client-server model
    - TCP port 90 or 443 for HTTPS
- one request and one response for each web object
- stateless
    - use cookies to maintain state
- message format: ASCII
- request methods: GET, POST, HEAD
- status codes

### HTTP connections

- HTTP 1.0 (non-persistent)
    - one object at most for each TCP connection
- HTTP 1.1 (persistent)
    - multiple requests with one connection
- HTTP 1.1 with pipelining
    - clients can send multiple requests without waiting for response
    - one RTT for TCP connection, one for HTTP page, one for all additional objects

### Web cache

Stores some information of web pages, usually faster to retrieve

## DNS

## Email

### Simple Mail Transfer Protocol (SMTP)

- send mail from user agent to server (TCP port 25)
- transfer emails (relay) from server to server (TCP port 587)
- uses TCP and ASCII commands similar to DICT
- can be used to manipulate email contents, security concern

### Post Office Protocol 3 (POP3)

- used by user agents to retrieve mail from server
- TCP port 110
- download and delete
- download and keep

### Internet Message Access Protocol (IMAP)

- similar to POP3, used by user agents to retrieve mails from server
- TCP port 143
- messages kept in the server in folders and synchronized

### Other Protocols

- HTTP, web mail
- proprietary protocols, Microsoft Exchange

## Peer-to-peer

BitTorrent, developed in 2001, was designed for peer-to-peer file sharing. 

### Data sharing examples

- gaming
- software updates

### BitTorrent

N+M machines participate in this network. N hosts have the actual file contents and are called **seeds**. All hosts are called **peers**. Instead of having a single server that sends the file to all clients, the seed will send a portion of the file to each peer that needs the file. Then, each peer can send its portion to other peers. Finally every host will assemble the portions and have the complete file. This can save tons of time. 

Each portion has a fixed size, except for the last part. Every part is also encrypted with a hash. There is a summary file (torrent file) that tells the total number of pieces, the hash for the entire file, and where to look for peers. 

Basic operations include finding peers and finding pieces. For finding pieces, each peer shares information about the identities of the pieces, so that they know who to find to get the piece. A group of peers is called a **swarm**. 

Some policies: ask for the rarest piece first, which will increase the overall health of a file. 

#### Implementation

BitTorrent is a open-source protocol, and uses TCP mostly. Some also use μTP which is a reliable UDP. 


## Blockchain

Blocks communicate to decide which block to add next to the chain. You have to do a lot of work to prove the history, and it is encouraged. This is why bitcoin mining was popular.  
