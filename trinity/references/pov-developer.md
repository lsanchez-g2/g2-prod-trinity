# POV Developer - Reference

The Developer lens cares about what breaks, what costs, and what scales. It is not about elegance for its own sake. Elegance that the next engineer cannot maintain is a liability.

## Feasibility framework

When asked "can we build this?", the answer is almost always yes. The real questions:

1. **In what time, with what team?** A senior can do in a sprint what a juniors-only team cannot do in a quarter.
2. **At what fixed cost?** Initial build, infra, third-party APIs.
3. **At what running cost?** Per-request cost, per-user cost, on-call burden.
4. **At what cost to future change?** Does this lock us into a stack, a vendor, a data model?
5. **At what risk?** What does "it broke at 2am" look like for this feature?

If any of these are unknown, name them as unknowns. Do not estimate confidently from a vacuum.

## Technical risk register

Pattern-match against this list when reviewing a proposal:

### Data
- **Schema lock-in**: changing a production schema later is 10x harder than getting it right
- **Soft deletes vs hard deletes**: pick one and apply it consistently
- **Idempotency**: any write that can be retried needs an idempotency key, period
- **Eventual consistency**: if the user reads after writing, can they see their write? If no, design for it.
- **PII**: classify on day one, encrypt in transit and at rest, audit access
- **Migrations**: zero-downtime requires backward-compatible schema changes (add column, deploy, backfill, deploy, drop column)

### API surface
- **Versioning**: pick a strategy before the second consumer arrives
- **Contracts**: typed, documented, with schemas. OpenAPI for REST, schema for GraphQL.
- **Rate limits**: design them in. Retro-fitting limits breaks consumers.
- **Pagination**: cursor over offset for anything that grows
- **Error taxonomy**: codes that mean something, messages safe to show users, details safe for debugging

### Frontend
- **State management**: server state ≠ client state ≠ URL state. Each has the right home.
- **Component contracts**: props in, events out. Avoid prop drilling beyond two levels.
- **Performance budget**: LCP < 2.5s, INP < 200ms, CLS < 0.1. Set, measure, regress on PRs.
- **Accessibility**: built in, not bolted on. Audit in CI.
- **Bundle**: code-split by route at minimum, by feature where it matters. Watch third-party weight.

### AI-specific
- **Model choice is a tradeoff matrix**: capability × latency × cost × controllability
- **Determinism**: temperature 0 is not deterministic across model versions. Pin model versions.
- **Eval harness**: every prompt change needs a regression set. No exceptions.
- **Prompt as code**: version it, review it, test it
- **Failure modes**: hallucination, refusal, overlong output, malformed structure, prompt injection. Plan for each.
- **Streaming**: design the UI for partial output. Plan for stop-mid-stream and resume.
- **Cost telemetry**: per-request token tracking from day one. Without it, costs surprise you.
- **Latency budget**: end-to-end p95 target. Model latency is one term in a larger sum.
- **Fallbacks**: what does the product do when the model is down, slow, or returning garbage?

### Operations
- **Observability triad**: metrics (rates, durations, errors), logs (structured, sampled), traces (request flow)
- **Alerting**: alert on user-facing symptoms, not internal causes. SLOs, not vibes.
- **Rollback**: every deploy needs a one-button rollback path. Database changes complicate this.
- **Feature flags**: ship dark, enable by cohort, kill instantly. Default-off for risky features.
- **Runbooks**: written before launch, tested in chaos exercises

## Build vs buy vs borrow

Default lean: borrow open source, buy commodity, build differentiated. Specific tests:

- **Build** when: it is core to the product wedge, requirements are unstable, vendor pricing scales badly with usage
- **Buy** when: it is solved well, requirements are stable, vendor risk is acceptable, scaling cost is acceptable
- **Borrow (OSS)** when: it has the maintainer momentum, license is compatible, security posture is reviewable

For AI specifically: model API (buy) is almost always right at the start. Self-host once: (a) cost crosses the threshold, (b) you need control the API does not give, or (c) data residency requires it. Not before.

## Common Developer pushbacks

The Developer is likely to push back when:

- "It's just a small feature" hides a data model change
- "We can refactor later" applies to something on the critical path
- The spec assumes synchronous behavior on something that should be async
- The AI feature has no eval, no fallback, and no cost telemetry
- The integration depends on a third-party SLA we have not read
- "Make it real-time" is asked for without defining acceptable lag
- Security or privacy is a checklist item at the end instead of a constraint at the start
- The error handling is "show a toast"
- The migration plan is "we'll figure it out"

### G2-specific Developer pushbacks
- The proposal touches review data without naming the consistency model (eventual vs strong) and the staleness budget
- AI generation is per-pageview when corpus-level caching with TTL is the obvious pattern
- The new surface does not specify canonical URL behavior, breaking SEO at scale
- Vendor-impacting changes have no API or webhook for vendors to react in their own systems
- Personalization is proposed without naming the cold-start behavior for new users or new categories
- The feature touches multiple review locales without naming the language model fallback (English-only model on Spanish reviews is a silent failure)
- Schema.org markup, structured data, or sitemap impact is missing from a buyer-surface change

## When to write code now vs. design first

Code-first when: the design space is well-understood, the question is "does this approach work", and a 2-hour spike resolves more than a week of meetings.

Design-first when: the design space is open, multiple valid architectures exist, the cost of the wrong choice is high, or the feature crosses team boundaries.

## Developer-specific output style

When producing Developer reasoning, name the concrete components, contracts, and failure modes. Quantify when possible (latency targets, cost estimates, complexity scores). If you say "this is hard", say what specifically is hard and why.
