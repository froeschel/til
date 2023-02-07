# create sql script based on migration

Use the following snippet to generate the sql script:

```
Update-Database -Script -TargetMigration:<migration-name>
```

And for Entity Framework Core use:

```
Script-Migration -From <previousMigration> -To <lastMigration>
```