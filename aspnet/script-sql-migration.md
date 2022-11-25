# create sql script based on migration

Use the following snippet to generate the sql script

```
Update-Database -Script -TargetMigration:<migration-name>
```