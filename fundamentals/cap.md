# CAP Theorem

CAP stands for:
- (C)onsistency: All nodes see the same data at the same time.
- (A)vailability: Every request to node receives a response.
- (P)artition Tolerance: The distributed system can continue to work even when some nodes of the system are failing. 

The theorem states that in a distributed system only two of the three characteristics can be achieved at the same time. This means one needs to make trade offs when designing a distributed system.

In practice a distributed system in the public cloud will always have the possibility of network and hardware failures, so this is an issue that needs to be addressed. This means that there are two characteristics to decide between. Do we want consistency or availability? Consistency makes sense, when we have a system that needs to have the correct updated values at any given time. This could be booking sites or financial systems like a trading platform. Availability on the other hand is a better choice when one wants to make sure that data is always available and it does not matter that some data is updated a bit later.