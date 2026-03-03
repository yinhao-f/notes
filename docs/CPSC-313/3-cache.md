# Cache

## Memory hierarchy

- Registers
    - fastest, smallest, most expensive
- L1 cache
- L2 cache
- L3 cache
- Main memory
- SSD
- HDD
    - slowest, biggest, cheapest

## Caching

Storing something for later use

### Cache misses

- Compulsory: first time access
- Capacity: cache full
- Conflict

### Cache size

- Disk access usually in 4 KB at a time
    - blocks or pages
- Cache's native size
    - 64 bytes usually
- Block size: unit in which data is stored in cache
    - called cache line size in hardware cache

### Locality

- Spatial locality
- Temporal locality
    - accessing the same data shortly after

### Cache location

- Hashing: too slow for hardware cache
- Hardware: mod by power of 2

### Cache index

- Number of slots
- Number of bits to represent each slot

### Eviction policy

LRU: Least recently used
LFU: Least frequently used