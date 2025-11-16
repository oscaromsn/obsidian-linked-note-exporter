# Timeout Settings.md (Depth 5)

Granular timeout configuration for different operations.

**Expected location:** `Architecture/Microservices/Timeout Settings.md`
**Depth:** 5 (deepest!)
**Parent:** Pool Config.md
**Inherited path:** ["Architecture", "Microservices"]

## Timeout Values

```yaml
timeouts:
  connect: 5000      # 5s connection timeout
  query: 30000       # 30s query timeout
  idle: 30000        # 30s idle timeout
  acquire: 10000     # 10s acquire timeout
```

## Important Note

**This file is at DEPTH 5.** If it appears at the root of the export instead of under `Architecture/Microservices/`, the implementation is broken and header context is NOT being propagated through the full chain.

