# Fault Tolerance.

- Replication
- Load balancer
- Master Slave - any server that crashes down -> redirect traffic to slave using last snapshot.

> What if both master and all replica crash at the same time.

One thing we can do if to allocate a new server and rebuild the same index on the new server.

> To make this work, we need to build and store a reverse index that map id to index. --> With this kind of information, we can rebuild the index fast.