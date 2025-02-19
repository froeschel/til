# Consistency Levels
1.	Strong Consistency:
    - Guarantees linearizability.
    - Reads are guaranteed to return the most recent committed version of an item.
    - Provides the highest consistency but with higher latency and lower availability.
2.	Bounded Staleness:
	- Guarantees that reads are not too out-of-date.
    - You can configure the staleness window in terms of time (seconds) or versions (operations).
    - Offers a balance between strong consistency and availability.
3.	Session Consistency:
    - Guarantees consistency within a single session.
    - Ensures monotonic reads, monotonic writes, and read-your-writes guarantees within a session.
    - Ideal for scenarios where a single user or device session needs consistent reads and writes.
4.	Consistent Prefix:
    - Guarantees that reads never see out-of-order writes.
    - If a write sequence is A, B, C, then a client will never see B, A, C.
    - Provides a lower consistency level than session but higher than eventual consistency.
5.	Eventual Consistency:
    - Guarantees that eventually, all replicas will converge.
    - Offers the lowest latency and highest availability.
    - Suitable for scenarios where the application can tolerate some level of inconsistency.