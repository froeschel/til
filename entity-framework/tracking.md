# Tracking vs. No Tacking

By default all items that are returned from a query are tracked. This means that any changes to the entity will be persisted on ``SaveChanges()``.
When entities are used in an read-only scenario they can be fetched with a no tracking query. This will improve performance, because no change tracking informations needs to be set up. Making a no tracking query can be achieved with ``.AsNoTracking()`` method.