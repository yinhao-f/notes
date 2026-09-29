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
    - K = $2^10$
    - M = $2^20$
    - G = $2^30$
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
- `ping`, `traceroute` reports RTT

## Jitter

Variation in latency and/or RTT

Causes:

- different paths for packets
- network congestion
- no packet prioritization
- poor hardware, old equipment
- wireless interference

## Delays

- Processing delay
  - fixed
- Queueing delay
  - variable
- Transmission delay
  - fixed if using same link
  - time it takes to get the data on the link
- Propagation delay
  - fixed if same link
- End-to-end delay
  - variable

### Total delay

$$ \frac {S} {1-U} $$

### Queueing delay
