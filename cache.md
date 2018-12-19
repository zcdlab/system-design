# Cache

80-20 Rule (https://stackoverflow.com/questions/43642044/80-20-rule-pareto-and-estimating-cache-size)

A high-end commercial server can ha ve up to 144GB of memory. When the cache is full, and we want to replace a data with a newer/hotter chunk - Least Recently Used (LRU) can be a reasonable policy for our system. Under this policy, we discard the least recently used chunk first.