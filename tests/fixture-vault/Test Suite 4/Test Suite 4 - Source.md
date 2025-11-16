# Test Suite 4: Header-less Files and Root Placement

This test validates Rule 3: Files linked before any H2+ header go to root, and their children inherit this empty header path.

## Expected Export Structure

```
Test Suite 4/
├── Preamble.md                       ← At root (linked before any H2+)
├── Introduction.md                   ← At root (linked before any H2+)
├── Glossary.md                       ← Depth 2, inherits root from Preamble
├── Terminology.md                    ← Depth 2, inherits root from Introduction
└── Content/
    ├── Main Article.md               ← Under header
    ├── References.md                 ← Depth 2, inherits ["Content"]
    └── Citations.md                  ← Depth 2, inherits ["Content"]
```

This document starts with some preamble files that are linked before any headers appear.

**Important files before headers:**
- [[Preamble]]
- [[Introduction]]

## Content

Now we have actual content under a header:
- [[Main Article]]

## Notes

**Link depth setting:** 2 or higher
**Header hierarchy:** Enabled

**Critical test validation:**
1. ✅ Preamble.md at root (no header context)
2. ✅ Introduction.md at root (no header context)
3. ✅ Glossary.md (linked from Preamble) ALSO at root (inherits empty path)
4. ✅ Terminology.md (linked from Introduction) ALSO at root (inherits empty path)
5. ✅ Main Article.md under `Content/` (has header context)
6. ✅ References.md under `Content/` (inherits ["Content"] from Main Article)

**This tests Rule 3:** Header-less links and their descendants go to root.