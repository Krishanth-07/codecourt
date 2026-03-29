---
name: generate-briefing
description: "Aggregates findings from all three specialist agents and generates a structured human briefing report before the merge decision."
---

# Generate Briefing

## Instructions

When all three specialist agents have completed their analysis:

1. **Collect all findings** - Gather reports from SecurityScout, PerfProbe, and QualityGuard.
2. **Count by severity** - Tally CRITICAL, HIGH, MEDIUM, LOW findings across all agents.
3. **Lead with the most critical** - Always present security findings first, then performance, then quality.
4. **Summarize clearly** - Give the engineer a clear picture in under 30 seconds of reading.
5. **Never suppress** - Every finding from every agent must appear in the briefing.
6. **End with decision prompt** - Always close with the human decision block.

## Output Format

---
## CodeCourt Review Briefing

**PR**: [title]
**Author**: [author]
**Files changed**: [count]

### Summary
- CRITICAL: [count]
- HIGH: [count]
- MEDIUM: [count]
- LOW: [count]

### Security Findings (SecurityScout)
[findings or None]

### Performance Findings (PerfProbe)
[findings or None]

### Quality Findings (QualityGuard)
[findings or None]

---
HUMAN DECISION REQUIRED: [ Merge ] [ Request Changes ] [ Reject ]
---
