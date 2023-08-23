# Partial Update of Document in Cosmos DB

Since version 3.23.0 the Cosmos SDK allows partial updates for documents. This makes it a lot easier to update properties of a specific documents. In order to make a partial update, the following code is needed.

```
ItemResponse<Product> response = await container.PatchItemAsync<Product>(
    id: "e379aea5-63f5-4623-9a9b-4cd9b33b91d5",
    partitionKey: new PartitionKey("road-bikes"),
    patchOperations: new[] {
        PatchOperation.Replace("/price", 355.45)
    }
);

Product updated = response.Resource;
```