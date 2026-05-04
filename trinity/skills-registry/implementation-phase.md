# Implementation Phase Skills

Skills for coding, testing, API building, technical architecture, and production implementation. Use these when the trio moves from "how it looks" to "how it's built."

## Primary Skills (Invoke automatically when recommended)

### `frontend-design` - Frontend implementation with design systems
**When to use:** Recommendation includes "implement the frontend", "build the UI", or "code the interface"
**Brand fit:** All brands
**Inputs needed:** Design specs, component requirements, framework (React/Vue/etc), design system
**Outputs:** Production-ready frontend code with tests and documentation
**Invoke when:** "Implement the X component", "Build the Y interface", "Code the Z page"
**Note:** This skill bridges design and code—use it when design + implementation are coupled

### `tdd-workflow` - Test-driven development
**When to use:** Recommendation emphasizes "test-driven", "write tests first", or quality/reliability are critical
**Brand fit:** G2 (enterprise reliability), any brand for core platform features
**Inputs needed:** Feature requirements, test scenarios, edge cases
**Outputs:** Tests + implementation following TDD red-green-refactor
**Invoke when:** "Build X with TDD", "Implement Y with comprehensive tests", "Test-first approach to Z"
**Best for:** Core platform features, payment flows, security-critical code, API contracts

### `api-docs` - API documentation and specification
**When to use:** Recommendation includes "document the API", "API spec", or "OpenAPI"
**Brand fit:** G2 (vendor integrations), any brand for platform APIs
**Inputs needed:** API endpoints, request/response schemas, authentication, examples
**Outputs:** OpenAPI spec, API reference docs, integration guides
**Invoke when:** "Document the X API", "Create API spec for Y", "Write integration docs for Z"

### `security-audit` - Security review and hardening
**When to use:** Recommendation includes "security", "audit", "vulnerabilities", or touches PII/payment data
**Brand fit:** All brands (review integrity, PII handling, payment data)
**Inputs needed:** Code to audit, threat model, compliance requirements (GDPR, PCI, etc)
**Outputs:** Security report, vulnerability list, remediation recommendations
**Invoke when:** "Security review of X", "Audit the Y feature", "Check Z for vulnerabilities"
**Critical for:** Payment flows, PII handling, vendor data access, review submission, advisor forms

### `finishing-a-development-branch` - Code completion and PR prep
**When to use:** Recommendation is "finish the implementation", "prepare for merge", or "ready for PR"
**Brand fit:** All brands
**Inputs needed:** Feature branch, remaining TODOs, test coverage requirements
**Outputs:** Completed implementation, tests passing, PR description, ready to merge
**Invoke when:** "Finish implementing X", "Complete the Y branch", "Prepare Z for review"

## Secondary Skills (Suggest to user if relevant)

### `code-review:code-review` - Code review
**When to use:** Developer POV recommends peer review before merge
**Best for:** Complex changes, architectural decisions, security-sensitive code
**Suggest when:** Implementation is done and needs review

### `git-workflow` - Git workflow and branching
**When to use:** Recommendation involves git strategy, branching, or release management
**Suggest when:** Planning feature branches, release strategy, or git workflow improvements

### `performance-analysis` - Performance optimization
**When to use:** Recommendation includes "performance", "speed", "latency", or "optimization"
**Best for:** High-traffic surfaces (Capterra category pages), database queries, API latency
**Suggest when:** Performance is a concern or bottleneck identified

### `mcp-builder` - Build MCP servers
**When to use:** Recommendation includes "build an integration", "MCP server", or tool/data access
**Best for:** Integrations with external systems, tool building, data connectors
**Suggest when:** Need to connect to external APIs or build custom tools

### `agent-architecture` - System architecture and design
**When to use:** Developer POV recommends "design the architecture" or "system design"
**Best for:** Large features, platform-level changes, microservices, architectural decisions
**Suggest when:** Implementation requires architectural planning first

### `vercel-deploy` / `vercel-react-best-practices` - Deployment and React patterns
**When to use:** Recommendation involves deployment or React-specific implementation
**Suggest when:** Deploying to Vercel or building React applications

## Brand-Specific Selection Logic

### Capterra (SMB, PPC-driven, high-traffic, SEO-critical)
**Implementation priorities:**
- **Performance** - 5.1M visits/month; every millisecond matters for PPC conversion
- **SEO integrity** - Organic search drives traffic; crawlability, schema, page speed are non-negotiable
- **PPC button reliability** - Revenue-generating clicks must be bulletproof
- **Scale** - 900-2000 category pages; solutions must scale

**Skill selection:**
```
IF brand = Capterra AND feature = category page change
  → Invoke `tdd-workflow` (too critical to break)
  → Follow with `performance-analysis` (page speed is conversion)
  → Follow with `security-audit` (if touches user data)

IF brand = Capterra AND feature = PPC button/conversion flow
  → Invoke `tdd-workflow` (revenue-critical)
  → Must include: Tracking verification, A/B test hooks, fallback behavior

IF brand = Capterra AND feature = new API endpoint
  → Invoke `api-docs` (vendor integrations)
  → Include: Rate limiting, auth, error codes, examples
```

**Avoid:**
- Experimental tech in production paths
- Database queries without indexes (scale concern)
- Client-side rendering for SEO-critical content

### Software Advice (Advisor-mediated, PPL, form-critical)
**Implementation priorities:**
- **Form reliability** - Lead generation is the revenue engine; forms must never fail
- **PII handling** - Forms capture detailed buyer data; GDPR, privacy, security critical
- **Advisor tooling** - CRM-like surfaces for advisor team; must be reliable and fast
- **Lead quality** - Instrumentation to measure qualification depth

**Skill selection:**
```
IF brand = Software Advice AND feature = advisor contact form
  → Invoke `tdd-workflow` (revenue-critical)
  → Follow with `security-audit` (PII handling)
  → Include: Form validation, error handling, submission tracking, PII encryption

IF brand = Software Advice AND feature = advisor dashboard
  → Invoke `frontend-design` (UI + implementation)
  → Follow with `performance-analysis` (advisor team uses this all day)

IF brand = Software Advice AND feature = lead routing logic
  → Invoke `tdd-workflow` (vendor trust depends on fair routing)
  → Include: Audit logging, dispute tracking, A/B test capability
```

**Avoid:**
- Client-side form validation only (forms must work with JS disabled)
- Storing PII in logs or analytics
- Lead routing logic without audit trails

### GetApp (Tech-forward SMB, comparison-driven, EU-leaning)
**Implementation priorities:**
- **Feature comparison** - Complex filtering and comparison tables are core value
- **EU data compliance** - GDPR, privacy-forward patterns
- **Mobile experience** - Tech buyers expect mobile parity
- **API integrations** - Tech buyers use APIs; vendor integrations matter

**Skill selection:**
```
IF brand = GetApp AND feature = comparison tables
  → Invoke `frontend-design` (complex interactions)
  → Include: Filter state management, save/share URLs, mobile collapse patterns

IF brand = GetApp AND feature = new API endpoint
  → Invoke `api-docs` (tech buyers read docs)
  → Include: Full examples, error codes, rate limits, SDKs if possible

IF brand = GetApp AND feature = EU user data
  → Invoke `security-audit` (GDPR compliance)
  → Include: Data retention, deletion, export, consent management
```

### G2 (Enterprise, subscription, data-rich, integrations)
**Implementation priorities:**
- **Enterprise reliability** - Downtime is unacceptable; testing and monitoring critical
- **Data accuracy** - Intent signals, Grid placement, review scores must be precise
- **Integration depth** - CRM integrations (Salesforce, HubSpot); API reliability matters
- **Performance at scale** - Large datasets, complex queries, dashboard rendering

**Skill selection:**
```
IF brand = G2 AND feature = intent data pipeline
  → Invoke `tdd-workflow` (data accuracy is revenue)
  → Invoke `agent-architecture` (system design for scale)
  → Include: Data validation, error handling, monitoring, alerting

IF brand = G2 AND feature = CRM integration
  → Invoke `mcp-builder` (integration building)
  → Follow with `api-docs` (vendor-facing docs)
  → Include: OAuth, webhooks, error handling, retry logic, rate limiting

IF brand = G2 AND feature = vendor dashboard metrics
  → Invoke `performance-analysis` (data-heavy dashboards)
  → Include: Query optimization, caching, lazy loading, export capabilities
```

**Avoid:**
- Unproven tech in core revenue paths (Grid, intent data)
- API changes without versioning and deprecation notices
- Data pipelines without monitoring and alerting

## Parallel Agent Spawning for Implementation

Spawn parallel agents when implementation has independent work streams:

### Pattern 1: Frontend + Backend in parallel
```
Task: "Implement the AI category summary feature"

↓ Spawn 2 agents in parallel:
  - Agent 1: `frontend-design` - Build the UI component
  - Agent 2: `tdd-workflow` - Build the backend API (batch generation, caching)
↓
Agents coordinate via API contract (agreed upfront)
↓
Integrate: Frontend consumes Backend API, test end-to-end
```

### Pattern 2: Core feature + documentation + security
```
Task: "Ship the new vendor API endpoint"

↓ Spawn 3 agents in parallel:
  - Agent 1: `tdd-workflow` - Implement the API endpoint
  - Agent 2: `api-docs` - Write the API documentation
  - Agent 3: `security-audit` - Security review of the implementation
↓
Agent 1 completes → Agents 2 and 3 review the implementation
↓
Synthesize: Documentation + security findings → fix issues → ship
```

### Pattern 3: Multi-platform implementation
```
Task: "Implement review submission for web and mobile"

↓ Spawn 2 agents in parallel:
  - Agent 1: `frontend-design` - Web implementation
  - Agent 2: `mobile-app` - Mobile implementation
↓
Both use same backend API (coordinate on API contract)
↓
Test both platforms, ensure consistent UX and data handling
```

### Pattern 4: Performance optimization across surfaces
```
Task: "Optimize category page load time"

↓ Spawn 3 agents in parallel:
  - Agent 1: `performance-analysis` - Frontend performance (JS, CSS, images)
  - Agent 2: `performance-analysis` - Backend performance (DB queries, caching)
  - Agent 3: `performance-analysis` - Infrastructure (CDN, server config, API latency)
↓
Synthesize: Identify bottlenecks, prioritize fixes, re-measure
```

## Selection Decision Tree

```
IF recommendation contains ["implement", "build", "code"]
  AND frontend/UI work
    → Invoke `frontend-design`
  
  AND backend/API work
    AND emphasizes testing/reliability
      → Invoke `tdd-workflow`
    AND needs documentation
      → Invoke `api-docs` (or spawn in parallel with TDD)
  
  AND security/PII/payment data involved
    → Invoke `security-audit` (or spawn in parallel)
  
  AND architecture design needed first
    → Invoke `agent-architecture` first, then implementation skills

IF recommendation contains ["test-driven", "TDD", "tests first"]
  → Invoke `tdd-workflow`

IF recommendation contains ["document API", "API spec", "integration guide"]
  → Invoke `api-docs`

IF recommendation contains ["security", "audit", "vulnerabilities"]
  → Invoke `security-audit`

IF recommendation contains ["performance", "optimize", "speed"]
  → Suggest `performance-analysis`

IF recommendation contains ["finish", "complete", "prepare for merge"]
  → Invoke `finishing-a-development-branch`

IF multiple independent work streams (frontend + backend, web + mobile)
  → Spawn parallel agents with appropriate skills
```

## Fallback Behavior

If the required skill is not installed:
1. **Notify:** "The `skill-name` skill would handle this better. Install: `claude skill install skill-name`"
2. **Offer:** "I can implement this inline, but without the specialized workflow. Proceed?"
3. **If user agrees:** Implement inline using standard practices
4. **Document trade-offs:** "With `tdd-workflow` installed, this would follow red-green-refactor and have better test coverage."

## Output Integration

When an implementation skill completes:
1. **Review the output** (code, tests, docs)
2. **Validate against POVs:**
   - Designer: Does the implementation match the design? Any UX regressions?
   - Developer: Is the code maintainable? Test coverage adequate? Performance okay?
   - PM: Does it solve the user problem? Any edge cases missed?
3. **Run validation experiments:** If recommendation included "validate assumption X", instrument the code to measure X
4. **Surface deployment considerations:**
   - Rollout strategy: Feature flag? Phased? A/B test?
   - Monitoring: What metrics to watch? What alerts to set?
   - Rollback plan: How to revert if it breaks?
5. **Provide next steps:** "Deploy to staging", "Run load tests", "Schedule code review"

**Example:**
```
User: "Implement the AI category summary feature for Capterra"

Trio recommendation: "Build with batch generation (not per-pageview), 24h TTL cache,
  citation links to top 3 products, eval harness with 95%+ accuracy threshold,
  fallback to no-summary for edge cases"
↓
Spawn 2 agents in parallel:
  - Agent 1: `frontend-design` - Build the UI (summary block, citations, "generated by AI" label)
  - Agent 2: `tdd-workflow` - Build backend (batch generation, eval harness, caching, fallbacks)
↓
Both complete:
  - Frontend: React component with responsive design, mobile-first, trust signals
  - Backend: API endpoint, batch job, caching layer, eval validation, error handling
↓
Trio validates:
  - Designer: "UI matches spec - citations clear, mobile works, trust signals present"
  - Developer: "Code is solid - test coverage 92%, performance acceptable, fallbacks work"
  - PM: "Ready to test assumption: Does this reduce time-to-first-click by 10%+?"
↓
Output to user: "Implementation complete [code links]. Next steps:
  1. Deploy to staging
  2. Run on 50 mid-sized categories (A/B test)
  3. Monitor: time-to-first-click, PPC CTR, lead quality
  4. Decision rule: If click time ↓10%+ AND lead quality holds → expand to 200 categories"
```

## Special Considerations by Feature Type

### Revenue-critical features (PPC buttons, forms, payment flows)
- **Always use `tdd-workflow`** - Cannot afford breakage
- **Always include `security-audit`** - Revenue + trust on the line
- **Include instrumentation** - Must measure conversion impact
- **Feature flag** - Must be able to turn off instantly
- **Monitoring + alerts** - Must know immediately if it breaks

### SEO-critical features (category pages, product pages, content)
- **Server-side rendering** - Crawlability non-negotiable
- **Performance testing** - Page speed is ranking factor
- **Schema markup** - Structured data for search engines
- **Canonical URLs** - Avoid duplicate content
- **Mobile-first** - Mobile indexing is primary

### PII-handling features (forms, profiles, advisor tools)
- **Always include `security-audit`** - Legal and trust implications
- **Encryption** - In transit and at rest
- **Data retention** - GDPR compliance, delete after X days
- **Audit logging** - Track access and changes
- **Privacy-by-design** - Minimize collection, maximize protection

### Integration features (APIs, webhooks, CRM connectors)
- **Always include `api-docs`** - Vendors need clear docs
- **Versioning** - APIs must be backward-compatible or versioned
- **Rate limiting** - Protect infrastructure
- **Error codes** - Clear, actionable error messages
- **Examples + SDKs** - Lower integration friction
