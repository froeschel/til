# Use Point Reads

If one needs to read a specific item from Cosmos, the most effecient way to do this is a point read. A point read is a key/value lookup using the item ID and partition key. The cost for a point read will be 1 RU, which is lower than a typical query. A discussion on point reads can be found [here](https://devblogs.microsoft.com/cosmosdb/point-reads-versus-queries/).