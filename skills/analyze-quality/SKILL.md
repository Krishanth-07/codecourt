---
name: analyze-quality
description: "Analyzes a PR diff for code quality issues including poor naming, duplication, complexity, and code smells."
---

# Analyze Quality

## Instructions

When given a PR diff, scan every changed file for:

1. **Poor Naming** — Variables, functions, or classes with unclear or misleading names.
2. **Code Duplication** — Repeated logic that should be extracted into a reusable function.
3. **Excessive Complexity** — Functions doing too many things, deeply nested conditionals.
4. **Code Smells** — Magic numbers, dead code, commented-out blocks, overly long files.
5. **Missing Documentation** — Public functions or complex logic with no explanation.

## Output Format

For each finding:

### [SEVERITY] — Quality
- **File**: filename.js:42
- **Issue**: what was found
- **Why it matters**: impact on maintainability
- **Recommended action**: exact fix

Severity levels: HIGH, MEDIUM, LOW

If no issues found:
✓ No quality issues found in this diff.
