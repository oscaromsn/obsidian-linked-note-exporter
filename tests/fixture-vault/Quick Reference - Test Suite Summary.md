# Quick Reference: Test Suite Summary

## 📁 File Organization

```
Test Files/
├── TEST SUITE INSTRUCTIONS - README.md  ← Start here!
├── Test Suite 1/
│   ├── Test Suite 1 - Source.md        ← Basic depth-2 inheritance
│   └── [6 linked files]
├── Test Suite 2/
│   ├── Test Suite 2 - Source.md        ← Multiple parents & duplication
│   └── [5 linked files]
├── Test Suite 3/
│   ├── Test Suite 3 - Source.md        ← Deep nesting (depth 5)
│   └── [6 linked files]
├── Test Suite 4/
│   ├── Test Suite 4 - Source.md        ← Header-less files
│   └── [7 linked files]
└── Test Suite 5/
    ├── Test Suite 5 - Source.md        ← Complex real-world scenario
    └── [13 linked files]
```

## 🎯 What Each Test Validates

| Suite | Validates         | Files | Depth | Complexity |
| ----- | ----------------- | ----- | ----- | ---------- |
| 1     | Basic inheritance | 7     | 2     | ⭐ Low      |
| 2     | Duplication       | 6     | 2     | ⭐⭐ Medium  |
| 3     | Deep chains       | 6     | 5     | ⭐⭐ Medium  |
| 4     | Root placement    | 8     | 2     | ⭐⭐ Medium  |
| 5     | All features      | 14    | 3     | ⭐⭐⭐ High   |

## ⚡ Quick Test Commands

For each suite, run with:

- ✅ Header hierarchy: **Enabled**
- ✅ Link depth: **As specified**
- ❌ Keep folder structure: **Disabled**

## 🔍 Key Test Patterns

### Pattern 1: Simple Chain

```
Source → File1 → File2
Expected: All under same header
```

### Pattern 2: Duplication

```
Source → File1 (under header A)
Source → File1 (under header B)
File1 → Child
Expected: Child appears under BOTH headers
```

### Pattern 3: Root Inheritance

```
Source (no header) → File1
File1 → Child
Expected: Both File1 and Child at root
```

### Pattern 4: Deep Chain

```
A → B → C → D → E
Expected: All under A's header
```

## ✅ Pass/Fail Checklist

Quick verification for each test:

**Suite 1:**

- [ ] Depth-2 files under parent's folder ✓

**Suite 2:**

- [ ] Shared file appears 3x ✓
- [ ] Children also appear 3x ✓

**Suite 3:**

- [ ] Depth-5 file NOT at root ✓
- [ ] All files under same header ✓

**Suite 4:**

- [ ] Header-less files at root ✓
- [ ] Their children also at root ✓
- [ ] Files under headers NOT at root ✓

**Suite 5:**

- [ ] Duplicated methodology appears 2x ✓
- [ ] Data analysis also appears 2x ✓
- [ ] PNG/SVG files at depth 3 ✓
- [ ] Multi-level headers work ✓


## 🚨 Critical Tests (Must Pass)

1. **Suite 1:** If this fails, basic feature is broken
2. **Suite 2:** If this fails, duplication is broken
3. **Suite 5:** If this fails, complex scenarios don't work

## 📊 Expected Export Structures (Summary)

### Suite 1

```
Test Suite 1/
├── Research/Literature/
│   ├── Literature Review.md
│   ├── Academic Database.md ← depth 2
│   └── Citation Guidelines.md ← depth 2
└── Implementation/Backend/
    ├── Backend API.md
    ├── Database Schema.md ← depth 2
    └── API Authentication.md ← depth 2
```

### Suite 2

```
Test Suite 2/
├── Issues/
│   ├── Bug 42.md
│   ├── Stack Trace.md ← depth 2
│   └── Error Logs.md ← depth 2
├── Documentation/
│   ├── Bug 42.md ← DUPLICATE
│   ├── Stack Trace.md ← DUPLICATE
│   └── Error Logs.md ← DUPLICATE
└── Testing/
    ├── Bug 42.md ← DUPLICATE
    ├── Stack Trace.md ← DUPLICATE
    └── Error Logs.md ← DUPLICATE
```

### Suite 3

```
Test Suite 3/
└── Architecture/Microservices/
    ├── User Service.md (d1)
    ├── Database Layer.md (d2)
    ├── Connection Pool.md (d3)
    ├── Pool Config.md (d4)
    └── Timeout Settings.md (d5) ← CRITICAL TEST
```

### Suite 4

```
Test Suite 4/
├── Preamble.md ← ROOT
├── Introduction.md ← ROOT
├── Glossary.md ← ROOT (d2, inherits)
├── Terminology.md ← ROOT (d2, inherits)
└── Content/
    ├── Main Article.md
    ├── References.md ← depth 2
    └── Citations.md ← depth 2
```

### Suite 5

```
Test Suite 5/
├── README.md ← ROOT
├── Getting Started.md ← ROOT (d2)
├── Research/
│   ├── Survey Paper.md
│   ├── Related Work.md (d2)
│   ├── Methodology.md ← DUPLICATE
│   └── Data Analysis.md (d2) ← DUPLICATE
└── Implementation/System Architecture/
    ├── System Design.md
    ├── Methodology.md ← DUPLICATE
    ├── Data Analysis.md ← DUPLICATE
    ├── API Layer.md (d2)
    ├── database.png (d3) ← NON-MD
    └── auth_flow.svg (d3) ← NON-MD
```

## 💡 Pro Tips

1. **Test incrementally:** Start with Suite 1, then 2, then 3...
2. **Use ZIP export:** Easier to inspect folder structure
3. **Compare side-by-side:** Expected vs actual structure
4. **Check file counts:** Each folder should have correct number of files
5. **Verify duplicates:** Count total files, not unique files

## 🐛 Common Failures

|Symptom|Likely Issue|
|---|---|
|All depth-2 at root|Header map not propagating|
|No duplication|Parent map using wrong data structure|
|Depth-5 at root|Iterative processing not working|
|Non-MD files missing|File type check too restrictive|
|Files under wrong headers|Header parsing logic broken|

## 📞 Next Steps

1. **Read:** TEST SUITE INSTRUCTIONS - README.md
2. **Setup:** Create test vault with all files
3. **Run:** Export each suite with specified settings
4. **Verify:** Compare output to expected structures
5. **Debug:** If fails, check common issues
6. **Iterate:** Fix and re-test until all pass

---

**All tests passing = Implementation ready! 🎉**
