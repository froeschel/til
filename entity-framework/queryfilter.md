# Global Query Filters in EF Core

<b>[From  documentation]</b> Global query filters are LINQ query predicates applied to Entity Types in the metadata model (usually in OnModelCreating). A query predicate is a boolean expression typically passed to the LINQ Where query operator. EF Core applies such filters automatically to any LINQ queries involving those Entity Types. EF Core also applies them to Entity Types, referenced indirectly through use of Include or navigation property. 

Common uses cases for using global query filters are multitenency and soft deletion of entities. 

Global query filters can be configured the following way.

``` 
modelBuilder.Entity<Blog>().HasQueryFilter(b => EF.Property<string>(b, "_tenantId") == _tenantId);
modelBuilder.Entity<Post>().HasQueryFilter(p => !p.IsDeleted);
 ```