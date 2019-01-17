# Cache

80-20 Rule (https://stackoverflow.com/questions/43642044/80-20-rule-pareto-and-estimating-cache-size)

A high-end commercial server can have up to 144GB of memory. We can use Memcache, which store cached items in memory. When the cache is full, and we want to replace a data with a newer/hotter chunk - Least Recently Used (LRU) can be a reasonable policy for our system. Under this policy, we discard the least recently used chunk first.

- Caching the top used data will be extremely helpful in the system.
- Small percentage of queries that will be responsible for most of the traffic.


Advanced:

- Build a simple Machine Learning model that try to predict the engagement of each query based on some metrics and cache these terms

    - Metrics:
        - simple counting
        - personalization
        - trending data
