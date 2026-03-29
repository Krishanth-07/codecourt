# CodeCourt ���️

> A multi-agent PR review system that briefs human engineers before they decide to merge.

## The Problem

Engineers merge code every day under time pressure. A single missed SQL injection, a memory leak, or a poorly named function can cost hours of debugging — or worse, a production incident. Human reviewers are good but not infallible. They get tired. They miss things.

## The Solution

CodeCourt deploys three specialist agents in parallel the moment a PR is ready for review:

- ��� **SecurityScout** — hunts for vulnerabilities, exposed secrets, and injection risks
- ⚡ **PerfProbe** — flags memory leaks, inefficient queries, and blocking operations
- ��� **QualityGuard** — catches poor naming, duplication, and code smells

A fourth agent — **CodeCourt itself** — aggregates all findings into a structured briefing and hands it to the human engineer. The human always makes the final call.

## How It Works
```
PR Submitted
     │
     ├──► SecurityScout  ──┐
     ├──► PerfProbe      ──┼──► CodeCourt Briefing ──► Human Decision
     └──► QualityGuard   ──┘
```

## Built With

- [gitagent](https://github.com/open-gitagent/gitagent) — git-native agent standard
- [gitclaw](https://github.com/open-gitagent/gitclaw) — agent runtime
- Claude Sonnet — underlying model

## Quick Start
```bash
# Clone the repo
git clone https://github.com/YOUR_USERNAME/codecourt.git
cd codecourt

# Validate the agent
gitagent validate

# View agent info
gitagent info

# Export as system prompt
gitagent export --format system-prompt

# Export for Lyzr
gitagent export --format lyzr
```

## Agent Structure
```
codecourt/
├── agent.yaml              # Manifest with compliance and SOD config
├── SOUL.md                 # CodeCourt identity and values
├── RULES.md                # Hard constraints and output format
├── DUTIES.md               # Role separation between agents
├── agents/
│   ├── security-scout/     # Security specialist
│   ├── perf-probe/         # Performance specialist
│   └── quality-guard/      # Code quality specialist
├── skills/
│   ├── analyze-security/
│   ├── analyze-performance/
│   ├── analyze-quality/
│   └── generate-briefing/
└── tools/
    └── fetch-pr.yaml
```

## Sample Briefing Output
```
## CodeCourt Review Briefing

PR: Add user authentication middleware
Author: dev-user
Files changed: 4

### Summary
- ��� CRITICAL: 1
- ��� HIGH: 2
- ��� MEDIUM: 1
- ��� LOW: 3

### Security Findings (SecurityScout)
### CRITICAL — Security
- **File**: middleware/auth.js:23
- **Issue**: Hardcoded JWT secret key found
- **Why it matters**: Anyone with repo access can forge tokens
- **Recommended action**: Move to environment variable immediately

### Performance Findings (PerfProbe)
✓ No performance issues found in this diff.

### Quality Findings (QualityGuard)
### MEDIUM — Quality
- **File**: middleware/auth.js:45
- **Issue**: Function handleAuth() does 6 different things
- **Why it matters**: Hard to test and maintain
- **Recommended action**: Split into smaller single-responsibility functions

---
HUMAN DECISION REQUIRED: [ Merge ] [ Request Changes ] [ Reject ]
```

## Design Principles

- **Human accountability first** — CodeCourt briefs, engineers decide. Always.
- **Separation of concerns** — Each specialist agent stays in its lane
- **Evidence-based findings** — No finding without a file and line reference
- **Compliance built in** — Full audit logging, human-in-the-loop enforcement
