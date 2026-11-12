# Shared Templates

House format for the deliverables. Graders mark against these headings.

---

## Architecture Decision Record

One file per decision, in `decisions/`, named `ADR-001-short-slug.md`.

```markdown
# ADR-00N: <the decision, stated as a decision>

- **Status:** Accepted | Superseded by ADR-00M
- **Date:** YYYY-MM-DD
- **Decision owner:**

## Context

What forced a decision here.

## Decision

What you decided, in one or two sentences, in the active voice.

## Alternatives considered

### Alternative A: <name>

- **How it would work:**
- **Why it is attractive:**
- **Why rejected:**

## Consequences

- **What this buys:**
- **What this costs:**
- **What it costs the client if I am wrong:**
- **What would make me revisit this:**

## What this survives
```

---

## Data findings

`data_findings.md`, unless the brief names it differently.

```markdown
# Data findings — <client>

## Summary

## Reconciliation

| Stage | Rows | Delta | Reason |
|---|---|---|---|

## Findings, ranked by risk

### F-01: <name> — Severity:

- **What it is:**
- **How I detected it:**
- **Scale:**
- **Effect on the client's number:**
- **What I did about it:**
- **Residual risk:**

## Looked wrong, is not wrong

| Apparent problem | Why it looks wrong | Why it is actually fine |
|---|---|---|

## Could not verify
```

---

## Client memo

`client_memo.md`. One page.

```markdown
# Memo to <client first name>

**From:**
**Date:**
**Subject:**

## What I found

## What I built

| What you asked for | Status | Evidence |
|---|---|---|

## What I recommend

## What I could not stand behind
```

Rules, applied by the grader:

- No tool, product, library or service names unless the brief says otherwise.
- No jargon that would need a glossary.
- One page.

---

## Improvement beyond the brief

`improvement.md`, plus the thing itself, built.

```markdown
# Improvement beyond the brief: <name>

## The problem it solves

## What I built

## What it is worth to <client>

## What it cost
```

---

## Measurement report

Where a brief sets a numeric target.

```markdown
# <Metric> report

## Target

## Method

- Hardware / container spec
- What was timed, from which event to which event
- Runs, warm or cold, and which figure is reported
- How to reproduce

## Results

| Scenario | Runs | Median | p95 | Worst | Target met? |
|---|---|---|---|---|---|

## Before / after

| Query / stage | Before | After | Change |
|---|---|---|---|

## Caveats
```
