# Jobify architecture

```mermaid
flowchart TD
  SRC[Registered public sources / manual input] --> INTAKE[Opportunity intake]
  INTAKE --> CLEAN[Normalize and validate]
  CLEAN --> DEDUPE[Deduplicate]
  DEDUPE --> EVIDENCE[Store source evidence and excerpts]
  EVIDENCE --> REQ[Requirement extraction and classification]
  REQ --> ELIGIBLE[Eligibility assessment]
  ELIGIBLE --> FIT[Skills-fit assessment]
  PROFILE[(Approved profile facts)] --> FIT
  PORTFOLIO[(Portfolio evidence)] --> MATCH[Select matching proof]
  FIT --> MATCH
  MATCH --> BUILD[Build tailored application package]
  BUILD --> HUMAN[Human review]
  HUMAN -->|Approved| NEXT[User-controlled application or outreach]
  HUMAN -->|Unsupported / incomplete| REVIEW[Review queue]
```

## Important boundaries

- Requirement, eligibility and fit results should retain the evidence used to reach them.
- Negated requirements must not be incorrectly treated as must-have criteria.
- Missing evidence for explicitly required skills routes to review rather than being inferred.
- A generated package is a draft for human review, not an automatically submitted application.
- Live source and Google Workspace integration status is separate from offline test results.
