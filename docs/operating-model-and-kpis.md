# 6. Operating model and KPIs

## Accountability

| Role | Accountability |
|---|---|
| Enterprise/Solution Architecture | Target architecture, integration patterns, guardrails and design decisions |
| Security/Vulnerability Management | Advisory validation, risk policy, exploit context and prioritisation |
| Cloud/Platform Operations | Asset inventory, platform patching and runtime evidence |
| Application/Product Owner | Application dependencies, testing, release and service acceptance |
| DevSecOps/Platform Engineering | CI/CD, SBOM, image rebuild, deployment automation |
| ITSM/Change Management | Assignment, approvals, SLA, exceptions and audit trail |
| Business Service Owner | Business criticality, outage trade-offs and risk acceptance |

## Core KPIs

| KPI | Definition |
|---|---|
| Asset coverage | In-scope assets with current inventory ÷ total in-scope assets |
| Owner coverage | Assets with accountable owner ÷ total in-scope assets |
| Advisory correlation time | Time from advisory intake to affected asset list |
| Mean time to assign | Time from confirmed exposure to accountable assignment |
| Mean time to remediate | Time from confirmed exposure to verified fix |
| Verified closure rate | Closed findings with required evidence ÷ all closed findings |
| Reopen rate | Findings reopened after failed validation or recurrence |
| Exception ageing | Age and count of approved, unexpired exceptions |
| Repeat vulnerability rate | Recurrence of same component issue after remediation |

## Reporting principles

- Segment by severity, exploit status, environment and business criticality.
- Show numerator, denominator, time window and data freshness.
- Separate confirmed exposure from potential matches.
- Separate patched, mitigated, accepted and not-applicable states.
- Do not count a ticket as closed until verification passes.
- Publish trends and bottlenecks, not only point-in-time totals.

## Governance

Every exception must include:
- Affected assets and service.
- Risk rationale.
- Named accountable owner and approver.
- Compensating controls.
- Remediation plan and target date.
- Expiry date and review cadence.

The objective is not to maximise the number of tickets closed. It is to reduce verified exposure while preserving service reliability.
