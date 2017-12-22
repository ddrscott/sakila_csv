## Sakila CSV

Generated from MySQL's Sakila sample database.

https://dev.mysql.com/doc/sakila/en/

The following statement generated the copy commands.

```sql
SELECT 
  concat(
    '\copy (select * from ',
    c.relname,
    ') to ''/path/to/sakila_csv/',
    c.relname,
    '.csv'' csv header'
  )
FROM pg_catalog.pg_class c
LEFT JOIN pg_catalog.pg_namespace n ON n.oid = c.relnamespace
WHERE c.relkind IN ('r','v')
  AND n.nspname <> 'pg_catalog'
  AND n.nspname <> 'information_schema'
  AND n.nspname !~ '^pg_toast'
  AND pg_catalog.pg_table_is_visible(c.oid)
ORDER BY 1;
```

## License

Same as the Sakila data's license:
https://dev.mysql.com/doc/sakila/en/sakila-license.html
