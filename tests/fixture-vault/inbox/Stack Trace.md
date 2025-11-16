# Stack Trace.md (Depth 2 - Inherits Multiple Contexts!)

Complete stack trace from the authentication error.

**Expected locations (DUPLICATED from parent):**
1. `Issues/Stack Trace.md`          ← Inherited from Bug 42 in Issues
2. `Documentation/Stack Trace.md`   ← Inherited from Bug 42 in Documentation
3. `Testing/Stack Trace.md`         ← Inherited from Bug 42 in Testing

**Parent:** Bug 42.md (which appears in 3 places)
**Inherited paths:**
- ["Issues"]
- ["Documentation"]
- ["Testing"]

## Stack Trace

```
Error: Invalid OAuth token
  at validateToken (auth.js:42)
  at handleLogin (controller.js:89)
  at processRequest (router.js:156)
```
