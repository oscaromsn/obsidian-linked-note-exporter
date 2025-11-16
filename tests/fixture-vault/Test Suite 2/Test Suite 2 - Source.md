# Test Suite 2: Multiple Parents Duplication

This test validates that files linked from multiple headers are duplicated, and their children inherit ALL parent contexts.

## Expected Export Structure

```
Test Suite 2/
├── Issues/
│   ├── Bug 42.md                    ← Shared file, appears here
│   ├── Stack Trace.md                ← Depth 2, inherits from Bug 42
│   └── Error Logs.md                 ← Depth 2, inherits from Bug 42
├── Documentation/
│   ├── Bug 42.md                    ← SAME file, duplicated here
│   ├── Stack Trace.md                ← Depth 2, duplicated from Bug 42
│   └── Error Logs.md                 ← Depth 2, duplicated from Bug 42
└── Testing/
    ├── Bug 42.md                    ← SAME file, duplicated again
    ├── Stack Trace.md                ← Depth 2, duplicated from Bug 42
    └── Error Logs.md                 ← Depth 2, duplicated from Bug 42
```

## Issues

Critical bugs to fix:
- [[Bug 42]]
- [[Memory Leak]]

## Documentation

Known issues documented:
- [[Bug 42]]
- [[API Quirks]]

## Testing

Test cases for:
- [[Bug 42]]
- [[Edge Cases]]

## Notes

**Link depth setting:** 2 or higher
**Header hierarchy:** Enabled

**Critical test validation:**
1. ✅ Bug 42.md appears in THREE locations (Issues/, Documentation/, Testing/)
2. ✅ Stack Trace.md (linked from Bug 42) ALSO appears in all THREE locations
3. ✅ Error Logs.md (linked from Bug 42) ALSO appears in all THREE locations
4. ✅ This demonstrates the combinatorial duplication effect

**This tests Rule 2:** Multiple Parent Duplication - children inherit ALL parent contexts.
