# Update Model

## Update Time

### Scenario
We have 100 million query per second and it is extremely resouce intersive which may hamper the request.

### Solution
As new query comes in, we can log in and keep track of frequency. Then log every 1000th query.

## Update Methods

We can and we should use Map Reduce to process all logging data and update the model.

To update the model in machine, we can update the model in each server offline, then up for serving. This causes downtime of the system.

> How to keep machine always serving?

- We can make a copy of the model to each other server. Then we can update it offline. Once done, we can switch to start using it and discard the old one.

- We can also have a master-slave configuration for each server pair. We can update the slave while master is providing service. ONce the update is complete, we can make slave as master, master as slave. Later, we can update our old master and switch again.



