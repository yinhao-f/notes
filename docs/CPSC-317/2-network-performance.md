# Network Performance

Metrics

- bandwidth
- throughput
- goodput
- latency
- round-trip-time
- jitter

## Note on units

- Data size: bytes, B, KB, MB, GB
    - K = $2^{10}$
    - M = $2^{20}$
    - G = $2^{30}$
- Data rate: bits per second, bps, Kbps, Mbps
    - K = $10^3$
    - M = $10^6$
    - G = $10^9$
- 1 byte (B) = 8 bits (b)

## Bandwidth

Maximum rate at which data can be sent over a link

## Throughput

Amount of data transfered in a given time

## Goodput

Amount of **useful** data transfered in a given time

- does not include headers and encoding costs
- does not include data loss and retransmissions

## Latency

Delay from data being sent to data being received

## Round-trip-time (RTT)

Latency for sending something and receiving something back

- easier to compute than one-way latency
- `ping` and `traceroute` report RTT

## Jitter

Variation in latency and/or RTT

Causes:

- different paths for packets
- network congestion
- no packet prioritization
- poor hardware, old equipment
- wireless interference

## Delay

- processing delay
    - examine a packet and find out where to direct it
    - from application layer to physical
    - fixed
- queueing delay
    - wait time for access to the link
    - after data is processed and before it is transmitted
    - variable
- transmission delay
    - time it takes to get the data on the link
    - after queueing
    - fixed if using the same link
- propagation delay
    - time to move each bit from source to destination on the medium
    - after transmission
    - fixed if using the same link
- end-to-end delay
    - sum of all delays
    - variable

## Traffic intensity

- rate at which data arrives
- rate at which router can process data
- helps understand how busy a link is
- queuing delay is related to this

### Calculation

- number of packets arriving per second ($a$)
- average packet size ($L$) in bits
- transmission rate: rate at which bits are sent per second ($R$)

$$ \text{Traffic intensity} = \frac {La} {R} $$

Bits arriving per second / bits sent per second

## Queuing problem

- packets may not be spaced out evenly
- packets may not be sent evenly (congestion in the link)

## Total delay and queuing delay

- assume packets arrive at an exponential distribution

$$ \text{Total delay} = \frac {S} {1-U} $$

- $S$ is the average service time when server is idle
- $U$ is server utilization, usually traffic intensity

$$ \text{Queuing delay} = \frac {S} {1-U} - S = \frac {US} {1-U} $$

Routers don't have infinite buffer, so packets may need to be dropped if they arrive too fast. Packets can also be corrupted and need to be dropped. 

