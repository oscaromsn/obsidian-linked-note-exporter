# Test Suite 5: Complex Real-World Project

This is a realistic project structure that combines multiple edge cases in one test.

## Expected Export Structure

```
Test Suite 5/
├── README.md                         ← Root (linked before headers)
├── Getting Started.md                ← Depth 2, from README (at root)
├── Research/
│   ├── Survey Paper.md               ← Depth 1
│   ├── Related Work.md               ← Depth 2, from Survey Paper
│   ├── Methodology.md                ← DUPLICATED (linked from 2 places)
│   └── Data Analysis.md              ← Depth 2, from Methodology
├── Implementation/
│   ├── System Design.md              ← Depth 1
│   ├── Methodology.md                ← DUPLICATED (same as above)
│   ├── Data Analysis.md              ← DUPLICATED (inherits from Methodology)
│   ├── API Layer.md                  ← Depth 2, from System Design
│   ├── database.png                  ← Depth 3, from API Layer (non-MD file!)
│   └── auth_flow.svg                 ← Depth 3, from API Layer (SVG file!)
└── Appendix/
    └── Diagrams/
        ├── Architecture Diagram.md   ← Depth 1
        └── system_arch.png           ← Depth 2, from Architecture Diagram
```

Project documentation with links to various resources.

Initial setup guide:
- [[README]]

## Research

Background research and methodology:
- [[Survey Paper]]
- [[Methodology]]

## Implementation

### System Architecture
- [[System Design]]
- [[Methodology]]

### Deployment
- [[Deployment Guide]]

## Appendix

### Diagrams
- [[Architecture Diagram]]

## Notes

**Link depth setting:** 3 or higher
**Header hierarchy:** Enabled

**This test combines:**
1. ✅ Header-less file (README) with child (Getting Started)
2. ✅ Multiple parents (Methodology appears under Research AND Implementation)
3. ✅ Duplication cascade (Data Analysis duplicated because parent is duplicated)
4. ✅ Deep nesting (depth 3 for image files)
5. ✅ Non-markdown files (PNG, SVG) at depth > 1
6. ✅ Multi-level headers (H2 and H3)
7. ✅ Files that only appear once (Survey Paper, System Design)

**Complexity score:** HIGH - This is a realistic, complex scenario that tests all features simultaneously.