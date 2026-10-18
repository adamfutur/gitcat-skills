# GitCat Review Checklist

Use this checklist selectively. Do not force every item into every review.

## Correctness
- Are branches, defaults, and boundary conditions correct?
- Are null, empty, malformed, or unexpected inputs handled?
- Are units, time zones, rounding, and conversions correct where relevant?
- Are state transitions and retries safe?
- Are errors propagated or handled consistently?

## Security and privacy
- Is authorization checked server-side for protected actions?
- Are inputs validated at trust boundaries?
- Are secrets, tokens, and personal data protected from logs and responses?
- Are SQL queries, shell commands, file paths, and HTML safely handled?
- Are authentication/session assumptions valid?
- Are dependency or cryptographic concerns supported by evidence?

## Reliability
- Are network calls, files, streams, and database resources handled safely?
- Are timeouts and retries bounded where needed?
- Can concurrent requests corrupt shared state?
- Can partial failure leave data inconsistent?
- Are migrations and schema changes compatible?

## Performance
- Is there an obvious N+1 query, unbounded loop, repeated expensive computation, or excessive memory use?
- Is caching correct and invalidated safely?
- Is work being done synchronously on a latency-sensitive path?
- Is the concern measurable or otherwise clearly impactful?

## Tests and maintainability
- Do tests cover the changed behavior and important failure paths?
- Are assertions meaningful, not just execution checks?
- Are public interfaces and types consistent?
- Does the change introduce unnecessary duplication or coupling?
- Are docs and configuration updated when behavior changes?

## Severity guidance
- **Critical:** likely catastrophic impact or broad compromise; immediate action needed.
- **High:** serious security, data integrity, or major functionality issue.
- **Medium:** meaningful bug or reliability issue under plausible conditions.
- **Low:** limited-impact defect or maintainability issue with a clear practical consequence.

Severity depends on likelihood, impact, exposure, and available mitigations. Explain the triggering conditions; do not assign severity based on code aesthetics alone.
