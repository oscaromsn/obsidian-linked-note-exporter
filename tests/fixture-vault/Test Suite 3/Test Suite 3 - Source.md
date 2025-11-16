# Test Suite 3: Deep Nesting Chain

This test validates that header context propagates through deep link chains (depth 5).

## Expected Export Structure

```
Test Suite 3/
└── Architecture/
    └── Microservices/
        ├── User Service.md           ← Depth 1
        ├── Database Layer.md         ← Depth 2 (from User Service)
        ├── Connection Pool.md        ← Depth 3 (from Database Layer)
        ├── Pool Config.md            ← Depth 4 (from Connection Pool)
        └── Timeout Settings.md       ← Depth 5 (from Pool Config)
```

**Link chain:** 
Source → User Service → Database Layer → Connection Pool → Pool Config → Timeout Settings

## Architecture

### Microservices
- [[User Service]]
- [[Payment Service]]

## Notes

**Link depth setting:** 5 or higher
**Header hierarchy:** Enabled

**Test validation:**
1. ✅ All files in the chain appear under `Architecture/Microservices/`
2. ✅ Each file inherits the same header path recursively: ["Architecture", "Microservices"]
3. ✅ Depth 5 file (Timeout Settings) is NOT at root
4. ✅ This validates Rule 4: Transitive Inheritance works through arbitrary depth