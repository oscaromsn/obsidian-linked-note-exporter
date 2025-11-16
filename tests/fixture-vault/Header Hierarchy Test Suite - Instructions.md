# Header Hierarchy Test Suite - Instructions

This comprehensive test suite validates the header hierarchy feature for link depth > 1 in the Obsidian Linked Note Exporter plugin.

## 📋 Test Suite Overview

| Test Suite  | Focus Area                     | Complexity | Key Validation                                                                      |
| ----------- | ------------------------------ | ---------- | ----------------------------------------------------------------------------------- |
| **Suite 1** | Basic Depth-2 Inheritance      | Low        | Files at depth 2 inherit parent's header context                                    |
| **Suite 2** | Multiple Parents & Duplication | Medium     | Files with multiple parents are duplicated, children inherit ALL contexts           |
| **Suite 3** | Deep Nesting (Depth 5)         | Medium     | Transitive inheritance works through arbitrary depth                                |
| **Suite 4** | Header-less Files              | Medium     | Files before any H2+ go to root, children inherit root placement                    |
| **Suite 5** | Complex Real-World Scenario    | **High**   | Combines all features: duplication, deep nesting, non-MD files, multi-level headers |


## 🚀 How to Use These Tests

### Setup Instructions

1. **Create a test vault** in Obsidian

2. **Copy each test suite** into separate folders:

    ```
    Test Vault/
    ├── Test Suite 1/
    │   ├── Test Suite 1 - Source.md
    │   ├── Literature Review.md
    │   ├── Backend API.md
    │   └── [other linked files]
    ├── Test Suite 2/
    │   ├── Test Suite 2 - Source.md
    │   └── [linked files]
    ├── Test Suite 3/
    ├── Test Suite 4/
    └── Test Suite 5/
    ```

3. **Install the plugin** (with your implementation changes)

4. **Run exports** with the specified settings for each test

### Running Tests

For each test suite:

1. **Open the source file** (e.g., "Test Suite 1 - Source.md")
2. **Run the export command**
3. **Configure export settings:**
    - ✅ Enable "Use header hierarchy"
    - ✅ Set link depth as specified in test
    - ❌ Disable "Keep folder structure"
    - Choose export format (directory or ZIP)
4. **Export to a test output folder**
5. **Verify the exported structure** matches the expected structure documented in each test

### Verification Checklist

For each test, verify:

- [ ] All files exported
- [ ] Folder structure matches expected layout
- [ ] Files at correct depth levels
- [ ] Duplicated files appear in all expected locations
- [ ] Non-markdown files (PNG, SVG) handled correctly
- [ ] No files missing or misplaced

## 📊 Expected Results by Test Suite

### Test Suite 1: Basic Depth-2 ✅

**Settings:** Link depth = 2, Header hierarchy = enabled

**Pass Criteria:**

- ✅ `Literature Review.md` under `Research/Literature/`
- ✅ `Academic Database.md` (depth 2) under `Research/Literature/`
- ✅ `Backend API.md` under `Implementation/Backend/`
- ✅ `Database Schema.md` (depth 2) under `Implementation/Backend/`

**Failure Indicators:**

- ❌ Depth-2 files at root instead of under parent's folder
- ❌ Depth-2 files in wrong header section

---

### Test Suite 2: Multiple Parents ✅

**Settings:** Link depth = 2, Header hierarchy = enabled

**Pass Criteria:**

- ✅ `Bug 42.md` appears in 3 locations (Issues/, Documentation/, Testing/)
- ✅ `Stack Trace.md` appears in same 3 locations (inherited from parent)
- ✅ `Error Logs.md` appears in same 3 locations (inherited from parent)

**Failure Indicators:**

- ❌ Bug 42 only appears once (duplication not working)
- ❌ Children don't appear in all parent locations
- ❌ Files appear in wrong combinations

---

### Test Suite 3: Deep Nesting ✅

**Settings:** Link depth = 5, Header hierarchy = enabled

**Pass Criteria:**

- ✅ All 5 files in the chain under `Architecture/Microservices/`
- ✅ `Timeout Settings.md` (depth 5!) under `Architecture/Microservices/`
- ✅ No files at root

**Failure Indicators:**

- ❌ Depth 5 file (`Timeout Settings.md`) at root
- ❌ Chain breaks at any depth level
- ❌ Files appear in wrong hierarchy

---

### Test Suite 4: Header-less Files ✅

**Settings:** Link depth = 2, Header hierarchy = enabled

**Pass Criteria:**

- ✅ `Preamble.md` at root (no folder)
- ✅ `Glossary.md` (depth 2, from Preamble) at root
- ✅ `Main Article.md` under `Content/`
- ✅ `References.md` (depth 2) under `Content/`

**Failure Indicators:**

- ❌ Header-less files go under a header
- ❌ Children of header-less files don't stay at root
- ❌ Files under headers appear at root

---

### Test Suite 5: Complex Real-World ✅

**Settings:** Link depth = 3, Header hierarchy = enabled

**Pass Criteria:**

- ✅ `README.md` at root
- ✅ `Getting Started.md` at root (inherits from README)
- ✅ `Methodology.md` appears in 2 locations (Research/ and Implementation/System Architecture/)
- ✅ `Data Analysis.md` appears in 2 locations (duplicated from parent)
- ✅ `database.png` (PNG, depth 3) under `Implementation/System Architecture/`
- ✅ `auth_flow.svg` (SVG, depth 3) under `Implementation/System Architecture/`
- ✅ Multi-level headers preserved (Appendix/Diagrams/)

**Failure Indicators:**

- ❌ Non-markdown files at wrong depth
- ❌ Duplication cascade doesn't work
- ❌ Multi-level headers flattened
- ❌ Any misplaced files

---

## 🐛 Debugging Tips

If tests fail, check:

1. **Console logs:** Look for errors during export
2. **Header map:** Verify the header map contains correct entries
3. **Parent map:** Check if parent-child relationships are tracked
4. **Depth tracking:** Ensure depth is correctly propagated
5. **File paths:** Verify path generation logic

### Common Issues

|Issue|Likely Cause|Fix|
|---|---|---|
|Depth-2 files at root|Header map not populated for depth > 1|Implement parent context propagation|
|No duplication|Parent map doesn't track multiple parents|Use `Set<string>` for parent storage|
|Deep nesting fails|Iterative processing doesn't converge|Process files in depth order or iterate until stable|
|Non-MD files ignored|File type check blocking inheritance|Remove MD-only restrictions from propagation|

## ✅ Success Criteria

The implementation is **fully correct** when:

1. ✅ **All 5 test suites pass** with expected folder structures
2. ✅ **No files are missing** from exports
3. ✅ **No files are misplaced** (wrong folder or wrong duplication)
4. ✅ **Backward compatibility maintained** (Suite 6A, 6B, 6C pass)
5. ✅ **Edge cases handled** (Suite 6D, 6E, 6F pass)
6. ✅ **Performance acceptable** (< 1s for < 1000 files)

## 📝 Reporting Results

When testing, document:

- ✅ Which tests passed
- ❌ Which tests failed
- 📸 Screenshots of exported folder structures
- 📋 Differences between expected and actual output
- 🐛 Any error messages or console logs

## 🔄 Iteration Tips

If implementation doesn't pass all tests:

1. **Start with Suite 1** (simplest case)
2. **Debug Suite 1** until it passes
3. **Move to Suite 2** (adds duplication)
4. **Progress through suites** in order
5. **Suite 5** should work if 1-4 pass

Don't try to fix everything at once—incremental progress is key!

## 📚 Additional Notes

### Creating Additional Test Cases

To add more tests:

1. Identify a specific edge case or scenario
2. Create a source file with clear expected structure
3. Create linked files with depth annotations
4. Document expected export structure
5. Add to this test suite

### Test File Naming

- Source files: `Test Suite N - [Description].md`
- Linked files: Descriptive names indicating purpose
- Add comments in files showing expected location

### Automation Potential

These tests can be automated by:

1. Running exports programmatically
2. Comparing folder structures with expected layouts
3. Generating pass/fail reports
4. Integrating with CI/CD

---

**Good luck with testing! 🚀**

If all 5 test suites pass, the implementation is correct and ready for merge!
