# Scale and Storage estimation

### Scale Estimation

Consider

- Daily active users (current)
- Daily active users (in 5 years) -- consider increase of users

> Make assumption of the size of data, so that you can estimatate the size of each day and the size would be taken in 5 years.


### Storage Estimation (partitioning the data) -- save/load the data in high efficiency and low latency

- Range Based Partitioning
> E.g. keep all record start with "A" in one partition.
> Pros: easy to implement
> Cons: some items have much more records than any others -> cannot fit in one partition.

- Max Capacity Partitioning
> E.g. we keep adding the data into one parition fisrt, then choose another one until it is full.
>
> Paritions may looks like:
> Server #1 - A - AABC
> Server #2 - AABD - BXA
> Server #3 - BXB - CDA
> 
> Since we have the range of each server, this still provides a pretty fast query.
>
> Pros: easy to implement, no worry about some ids query more frequently
> Cons: it still has the hotspot problem, for example, the same query might be ran multiple times. --> high load of one server compared to others.

- Hash Based Partitioning + consistent hashing

> Each record passes to a hash function, which generates a server number as id to that record. As we makes sure the number is generated randomly and distributed equally, each server has cloese number of records. Then the traffic would nearly be equal distributed.



Keep 20% or 30% capacity left (we don't want to go above 70% or 80% of total capacity of our storage system).