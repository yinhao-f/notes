# Network Address Translation (NAT)

- ran out of IPv4 addresses
- instead of switching to IPv6, decided to use tricks to make IPv4 work
- not every host needs a unique IP address
- solution
    - all hosts in a network share a single IP address
    - the edge router that connects to ISP has it
    - hosts have private addresses instead

## Reading

4.3.4

## Learning goals

- explain an IP header's role in NAT
- trace how network and transport headers for an IP network are used and changed in NAT
- what happens when a remote machine wants to connect to a server behind a NAT router
- shortcomings of NAT
- why application layer gets involved in NAT (P2P)

## Identifying connection

- source IP & port
- destination IP & port
- protocol, TCP or UDP
- local or remote
    - incoming messages: local is receiver
    - outgoing: local is sender

## Handling of messages

- when sending message, router converts source IP to public IP
    - converts port to an available port
    - adds table entry for source & dest IP & port, protocol, NAT IP & port
- when receiving message, router looks up the table and coverts dest IP & port to local IP & port

## Port forwarding

- when someone from the outside wants to connect to a server inside a NAT
    - NAT cannot find an entry in the table
- solution
    - add a fixed rule
    - Universal Plug and Play (UPnP)
    - table entry: when remote wants to connect to public IP with port, forward to local IP and port

## NAT problems

- breaks layering
    - routers shouldn't change IP or port
- security concern
    - port forwarding allows anyone to connect
    - vulnerable to attacks

## Application

- some application layer protocols advertise IP address in messages
    - P2P (requires manual setup)
    - internal host advertises their address
