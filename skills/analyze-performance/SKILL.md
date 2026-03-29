---
name: analyze-performance
description: "Analyzes a PR diff for performance anti-patterns including inefficient loops, memory leaks, unoptimized queries, and blocking operations."
---

# Analyze Performance

## Instructions

When given a PR diff, scan every changed file for:

1. **Inefficient Loops** — Nested loops on large datasets, repeated computations inside loops.
2. **Memory Leaks** — Event listeners not removed, unclosed connections, growing caches.
3. **Unoptimized Queries** — N+1 queries, missing indexes, unfiltered large fetches.
4. **Blocking Operations** — Synchronous calls in async contexts, long-running tasks on main thread.
5. **Unnecessary Re-renders** — Missing memoization or excessive state updates in UI code.

## Output Format

For each finding:

### [SEVERITY] — Performance
- **File**: filename.js:42
- **Issue**: what was found
- **Why it matters**: impact on speed or memory
- **Recommended action**: exact fix

Severity levels: CRITICAL, HIGH, MEDIUM, LOW

If no issues found:
✓ No performance issues found in this diff.
