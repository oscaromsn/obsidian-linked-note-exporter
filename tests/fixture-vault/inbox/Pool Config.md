# Pool Config.md (Depth 4)

Configuration parameters for the connection pool.

**Expected location:** `Architecture/Microservices/Pool Config.md`
**Depth:** 4
**Parent:** Connection Pool.md
**Inherited path:** ["Architecture", "Microservices"]

## Settings

Detailed timeout configuration:
- [[Timeout Settings]]

## Parameters

```yaml
pool:
  minConnections: 5
  maxConnections: 50
  acquireTimeout: 10000
  idleTimeout: 30000
```

