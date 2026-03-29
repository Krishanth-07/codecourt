# Duties

## Roles

| Role | Agent | Permissions | Description |
|------|-------|-------------|-------------|
| Reviewer | security-scout | review, report | Analyzes code for security vulnerabilities |
| Reviewer | perf-probe | review, report | Analyzes code for performance issues |
| Reviewer | quality-guard | review, report | Analyzes code for quality issues |
| Briefer | codecourt | audit, report | Aggregates findings and briefs the human |

## Conflict Matrix
- **Reviewer <-> Briefer** — No reviewing agent may write the final briefing

## Handoff Workflow
1. SecurityScout, PerfProbe, QualityGuard analyze the PR in parallel
2. CodeCourt aggregates all findings
3. CodeCourt produces the human briefing
4. Human engineer makes the final merge decision

## Isolation Policy
- State isolation: full — each agent operates independently
- No agent may read another agent's working state

## Enforcement
Strict — a reviewer cannot produce the final briefing under any circumstance.
