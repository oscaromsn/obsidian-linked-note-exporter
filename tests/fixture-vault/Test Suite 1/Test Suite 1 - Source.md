# Test Suite 1: Basic Depth-2 Inheritance

This test validates that files at depth 2 inherit their parent's header context.

## Expected Export Structure

```
Test Suite 1/
├── Research/
│   ├── Literature Review.md
│   ├── Academic Database.md          ← Depth 2, from Literature Review
│   └── Citation Guidelines.md        ← Depth 2, from Literature Review
└── Implementation/
    ├── Backend API.md
    ├── Database Schema.md            ← Depth 2, from Backend API
    └── API Authentication.md         ← Depth 2, from Backend API
```

## Research

### Literature
- [[Literature Review]]
- [[Data Collection Methods]]

## Implementation

### Backend
- [[Backend API]]
- [[Database Design]]

## Notes

**Link depth setting:** 2 or higher
**Header hierarchy:** Enabled

**Test validation:**
1. ✅ Literature Review.md should be under `Research/Literature/`
2. ✅ Academic Database.md (linked from Literature Review) should also be under `Research/Literature/`
3. ✅ Backend API.md should be under `Implementation/Backend/`
4. ✅ Database Schema.md (linked from Backend API) should also be under `Implementation/Backend/`