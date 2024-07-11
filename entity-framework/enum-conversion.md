### Enum Value Conversions

Value converters allow property values to be converted when reading from or writing to the database. This conversion can be from one value to another of the same type (for example, encrypting strings) or from a value of one type to a value of another type (for example, converting enum values to and from strings in the database) [source](https://learn.microsoft.com/en-us/ef/core/modeling/value-conversions?tabs=data-annotations).

In pour project we use value converison for enums when storing them in the database. We do this in order to get a better overview of the data when looking at data sets in the database. A conversion in EF core and be set up using this code in  DbContext.OnModelCreating.


```
//Conversion for enums
modelBuilder.Entity<Portal>().Property(p => p.Type).HasConversion<string>();
```