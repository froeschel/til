# Event Grid Retry
Event Grid will try to deliver a message at least once. When an event subscriber does not reply within 30 seconds, the message is queued for retry. If the delivery keeps failing, Event Grid uses an exponential backoff retry policy [1 minute, 5 minutes, 10 minutes, 30 minutes]. This gives a chalenge when having an event subscription that uses a long running operation and does not responds within 30 seconds. 
This retry schedule can not be changed. What can be changed is the maximum number of retries.
