# HSET

The Redis Hset command is used to assign values to fields in a hash table.

## Syntax

```
HSET key field value [field value ...]
```

## Return

If the field is a newly created field in the hash table and the value is successfully set, return 1. If the field in the hash table already exists and the old value has been overwritten by the new value, return 0.