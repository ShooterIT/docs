```yaml
apiVersion: app.redislabs.com/v1alpha1
kind: RedisEnterpriseDatabase
metadata:
  name: redb
  labels:
    app: redis-enterprise
spec:
  # Memory size of the database.
  memorySize: 256MB

  # Number of shards in the database.
  shardCount: 1

  # Determines whether replication will be enabled for the database.
  replication: false
```
