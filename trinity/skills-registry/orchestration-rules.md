# Orchestration Rules

This file defines the meta-logic for how the Product Trio skill orchestrates sub-skills: when to invoke automatically vs suggest, how to coordinate parallel agents, when to load which phase registry, and how to handle failures.

## Phase Detection

The trio must first identify which phase(s) the task belongs to. Most tasks touch multiple phases.

### Detection by Action Verbs

| Verbs | Phase | Load Registry |
|-------|-------|---------------|
| research, investigate, explore, understand, analyze competitors | Discovery | `discovery-phase.md` |
| design, wireframe, prototype, mock up, sketch | Design | `design-phase.md` |
| implement, build, code, develop, write tests | Implementation | `implementation-phase.md` |
| validate, test, measure, verify, A/B test | Validation | `validation-phase.md` |

### Detection by Artifacts

| Artifact Mentioned | Phase | Load Registry |
|--------------------|-------|---------------|
| research report, competitive analysis, spec, opportunity | Discovery | `discovery-phase.md` |
| wireframe, mockup, prototype, design, UI | Design | `design-phase.md` |
| code, API, tests, implementation | Implementation | `implementation-phase.md` |
| metrics, A/B test, performance report, validation plan | Validation | `validation-phase.md` |

### Multi-Phase Tasks

Many tasks span multiple phases. Load ALL relevant registries and coordinate across them.

**Example: "Build and test the AI category summary feature"**
- Phases: Design + Implementation + Validation
- Load: `design-phase.md`, `implementation-phase.md`, `validation-phase.md`
- Orchestration:
  1. Design: Invoke `web-prototype-taste-brutalist` for UI
  2. Implementation: Invoke `tdd-workflow` for backend (in parallel with design)
  3. Validation: After both complete, invoke `performance-analysis` + A/B test plan

## Automatic Invocation vs Suggestion

### Invoke Automatically (No User Confirmation)

Invoke a sub-skill automatically when **all** of these are true:
1. The trio's recommendation explicitly calls for the artifact the skill produces
2. The skill is in the "Primary Skills" section of the phase registry
3. The inputs needed are available or can be inferred from context
4. The skill execution is clearly the next step (not optional or exploratory)

**Examples:**
- Recommendation: "Prototype this with Capterra's aesthetic" → Invoke `web-prototype-taste-brutalist`
- Recommendation: "Implement with TDD" → Invoke `tdd-workflow`
- Recommendation: "Document the API" → Invoke `api-docs`
- Recommendation: "Research how competitors handle X" → Invoke `competitive-analysis`

### Suggest (Ask User First)

Suggest a sub-skill (don't invoke automatically) when:
1. The skill is in the "Secondary Skills" section
2. The skill might be helpful but isn't directly called for
3. The user might want to do it themselves or differently
4. The skill requires significant time/cost investment

**Examples:**
- "This would benefit from `deep-research` for deeper insights. Should I run it?"
- "Consider using `ckm-design-system` if you're building reusable components."
- "The `sparc-methodology` skill could help structure this complex problem. Want to use it?"

### Never Invoke

Never invoke a sub-skill when:
1. It's not installed (suggest installation instead)
2. The trio is in pure reasoning/analysis mode (no artifact production yet)
3. The user explicitly said not to use sub-skills this session
4. The skill would duplicate work already done in the current session

## Parallel vs Sequential Execution

### When to Spawn Parallel Agents

Spawn skills in parallel (same turn, multiple Agent tool calls) when:
1. **Independent work streams** - Tasks don't depend on each other's outputs
2. **Time-sensitive** - Waiting for sequential execution would be too slow
3. **Comparative analysis** - Exploring multiple approaches simultaneously

**Examples:**
- Design + Implementation in parallel (if API contract is defined)
- Multiple competitive analyses (5 competitors → 5 agents)
- Performance + Security + Cost analysis (independent validations)
- Design variants exploration (3 prototypes with different aesthetics)

**Code pattern:**
```
Spawn in SAME response turn:
  Agent 1: Do task A
  Agent 2: Do task B
  Agent 3: Do task C

Wait for all → Synthesize results
```

### When to Execute Sequentially

Execute skills sequentially when:
1. **Dependencies** - Task B needs Task A's output
2. **Refinement** - Second task builds on first's findings
3. **Gated approval** - User needs to review before proceeding

**Examples:**
- Research → Design → Implementation (each informs the next)
- Wireframe → User feedback → High-fidelity prototype
- Implementation → Security audit → Fix issues → Re-audit
- Discovery → Validate riskiest assumption → IF validated THEN proceed

**Code pattern:**
```
Turn 1: Invoke Skill A → wait for output
Turn 2: Use output from A to invoke Skill B → wait for output  
Turn 3: Synthesize A + B → recommendation
```

## Coordination Patterns

### Pattern 1: Discovery → Recommend → Execute

**Use when:** User asks a product question that requires analysis before action

```
Turn 1: Trio analyzes with three POVs → Disagreement → Recommendation
Turn 2: User approves recommendation
Turn 3: Invoke relevant skills to execute (design, implementation, validation)
```

**Example:**
```
User: "Should we add AI summaries to Capterra category pages?"

Turn 1: Trio analysis
  - Discovery phase load: Check if competitive analysis is needed
  - If yes: Invoke `competitive-analysis` → feed into POVs
  - POV Designer: [analysis]
  - POV Developer: [analysis]
  - POV PM: [analysis]
  - Disagreement: [tensions]
  - Recommendation: "Yes, launch with [specific approach]"

Turn 2: User: "Go ahead and build it"

Turn 3: Orchestrate execution
  - Invoke `web-prototype-taste-brutalist` (design)
  - Invoke `tdd-workflow` (implementation) in parallel
  - After both: Invoke `performance-analysis` + A/B test plan (validation)
```

### Pattern 2: Execute → Validate → Iterate

**Use when:** User asks to build something specific (decision already made)

```
Turn 1: Understand requirements → Load relevant phase registries
Turn 2: Invoke implementation skills
Turn 3: Invoke validation skills → Report results
Turn 4: If validation fails → Iterate (fix issues) → Re-validate
```

**Example:**
```
User: "Build the vendor onboarding flow for Software Advice"

Turn 1: Trio clarifies requirements
  - Form fields needed
  - PII handling requirements
  - Lead quality goals

Turn 2: Execute in parallel
  - Invoke `frontend-design` (form UI)
  - Invoke `tdd-workflow` (form backend + lead routing)

Turn 3: Validate
  - Invoke `security-audit` (PII handling)
  - Invoke `browser-test` (cross-browser)
  - Invoke `verification-quality-assurance` (functionality)

Turn 4: Validation results → Fix any issues → Re-validate if needed
```

### Pattern 3: Parallel Exploration → Converge → Decide

**Use when:** Disagreement requires evidence; multiple approaches should be tested

```
Turn 1: Trio surfaces disagreement with multiple valid approaches
Turn 2: Spawn parallel agents to explore each approach
Turn 3: Compare results → Make informed decision
Turn 4: Execute the chosen approach
```

**Example:**
```
User: "How should we approach the AI recommendation feature?"

Turn 1: Trio disagrees
  - Designer: "Ethnographic research to understand user needs" (slow, deep)
  - Developer: "Build and instrument a prototype" (fast, learn by doing)
  - PM: "Competitive analysis + user interviews" (balanced)

Turn 2: Spawn 3 agents in parallel
  - Agent 1: `deep-research` on user behavior (Designer approach)
  - Agent 2: `web-prototype` + instrumentation (Developer approach)
  - Agent 3: `competitive-analysis` + 10 user interviews (PM approach)

Turn 3: Compare findings
  - Research found: [insights]
  - Prototype revealed: [insights]
  - Competitive + interviews: [insights]
  - Synthesize: Which approach uncovered the real need?

Turn 4: Build final version informed by all three approaches
```

### Pattern 4: Iterative Refinement

**Use when:** Feature is complex and will need multiple rounds

```
Turn 1: Build MVP version
Turn 2: Test with small group → Gather feedback
Turn 3: Refine based on feedback
Turn 4: Expand test → Validate
Turn 5: Ship to 100%
```

**Example:**
```
User: "Launch the AI category summaries on Capterra"

Iteration 1: MVP
  - Invoke `web-prototype-taste-brutalist` (simple UI)
  - Invoke `tdd-workflow` (basic generation)
  - Test on 10 categories, 1 week

Iteration 2: Refine based on feedback
  - Users want citations → Add citation links
  - Users skeptical of AI → Add "Generated by AI" label + human review process
  - Test on 50 categories, 2 weeks

Iteration 3: Scale
  - Validation passes → Expand to 200 categories
  - Monitor closely for 1 month

Iteration 4: Full rollout
  - Success confirmed → Ship to all 900-2000 categories
```

## Cross-Phase Integration

### Discovery → Design

Discovery outputs feed into design:
- **Competitive analysis** → Informs UI patterns, trust signals, positioning
- **User research** → Informs information architecture, content hierarchy
- **Opportunity framing** → Defines what to design

**Integration:**
```
1. Invoke discovery skill (e.g., `competitive-analysis`)
2. Read output
3. Feed findings into Designer POV
4. Designer POV uses findings to inform design recommendations
5. Invoke design skill with context from discovery
```

### Design → Implementation

Design outputs feed into implementation:
- **Wireframes** → Define structure for code
- **Prototypes** → Provide visual spec for implementation
- **Design system** → Defines components and patterns to use

**Integration:**
```
1. Invoke design skill (e.g., `web-prototype-taste-brutalist`)
2. Read output (HTML/CSS/JS)
3. Feed into Developer POV
4. Developer POV assesses feasibility, performance, maintainability
5. Invoke implementation skill (e.g., `tdd-workflow`) with design as input
```

### Implementation → Validation

Implementation outputs feed into validation:
- **Instrumentation** → Enables metrics collection
- **Feature flags** → Enable A/B testing
- **Staging deployment** → Allows testing before production

**Integration:**
```
1. Invoke implementation skill (e.g., `tdd-workflow`)
2. Ensure instrumentation is in place (metrics, logging)
3. Deploy to staging/canary
4. Invoke validation skill (e.g., `performance-analysis`)
5. Validation results → Inform decision (ship/iterate/kill)
```

### Validation → Discovery (Feedback Loop)

Validation results can trigger new discovery:
- **A/B test fails** → Research why (user interviews, competitive analysis)
- **Performance issues** → Investigate bottlenecks (profiling, analysis)
- **Unexpected user behavior** → Ethnographic research to understand

**Integration:**
```
1. Validation reveals unexpected result
2. Invoke discovery skill to understand why
3. Discovery findings → Update hypothesis
4. Iterate: New design/implementation based on learnings
5. Re-validate with updated approach
```

## Failure Handling

### Skill Not Installed

```
IF skill is recommended AND skill not installed:
  1. Check if user has capability to install: "Install `skill-name` with: claude skill install skill-name"
  2. Offer fallback: "I can do this inline, but it won't have the specialized workflow. Proceed?"
  3. If user declines: Suggest alternative skill OR do inline
  4. Note in output: "This would be better with `skill-name` installed"
```

### Skill Execution Fails

```
IF skill invocation fails:
  1. Read error message
  2. Determine if it's recoverable:
     - Missing input? → Ask user for input → Retry
     - Skill bug? → Report to user, offer inline fallback
     - User cancellation? → Respect choice, ask what to do instead
  3. Surface in trio analysis: "Attempted to use X skill but [reason]. Proceeding inline."
```

### Parallel Agent Timeout

```
IF parallel agents spawned AND one times out:
  1. Don't wait indefinitely
  2. Proceed with completed agents' outputs
  3. Note which agent didn't complete
  4. Offer to retry the timed-out agent OR proceed without it
```

### Validation Fails

```
IF validation skill shows failure:
  1. Surface in Disagreement: "Validation disproved our hypothesis"
  2. Three options:
     a. Iterate: Fix issues and re-validate
     b. Pivot: Try a different approach
     c. Kill: Hypothesis was wrong, abandon feature
  3. Recommendation should include which option and why
  4. PM POV should calculate opportunity cost of each option
```

## Brand-Aware Orchestration

Brand context influences orchestration strategy:

### Capterra (SMB, PPC, high-traffic, SEO-critical)
**Orchestration priorities:**
- **Speed** - Fast iterations, time-boxed research
- **Validation** - Always measure PPC impact and page speed
- **Scale** - Solutions must work at 900-2000 categories, 5.1M visits/month

**Pattern:**
```
Discovery: Quick competitive scans (not exhaustive)
Design: Conversion-optimized, scan-first aesthetics
Implementation: Performance-critical, SEO-aware
Validation: A/B test with PPC CTR + page speed metrics
```

### Software Advice (Advisor-mediated, PPL, form-driven)
**Orchestration priorities:**
- **Trust** - Editorial quality, advisor neutrality
- **Form optimization** - Forms are revenue engine
- **Lead quality** - Vendor satisfaction depends on it

**Pattern:**
```
Discovery: Editorial depth, advisor model research
Design: Trust signals, form optimization, editorial aesthetics
Implementation: PII handling, form reliability critical
Validation: Form fill rate + lead quality metrics
```

### GetApp (Tech-forward SMB, comparison-driven)
**Orchestration priorities:**
- **Comparison clarity** - Feature matrices, filtering
- **Technical depth** - More than Capterra, less than G2
- **Mobile** - Tech buyers expect mobile parity

**Pattern:**
```
Discovery: Feature taxonomy research, comparison patterns
Design: Filter-heavy, comparison-optimized
Implementation: Mobile-first, complex state management
Validation: Comparison usage + mobile experience metrics
```

### G2 (Enterprise, subscription, data-rich)
**Orchestration priorities:**
- **Depth** - Enterprise buyers expect comprehensive data
- **Reliability** - Downtime is unacceptable
- **Integration** - CRM integrations, APIs matter

**Pattern:**
```
Discovery: Exhaustive research (not quick scans)
Design: Enterprise polish, data density, professional aesthetics
Implementation: Test-driven, architecture-first, reliability critical
Validation: Data accuracy + vendor value + integration quality metrics
```

## Decision Rules for Orchestration

### Should I invoke a skill automatically?

```
IF (recommendation explicitly calls for skill's artifact)
  AND (skill is in Primary Skills section)
  AND (inputs are available or inferrable)
  AND (skill is installed OR can fallback inline)
  AND (user hasn't said "no sub-skills this session")
THEN invoke automatically
ELSE suggest to user
```

### Should I spawn parallel agents?

```
IF (multiple independent work streams)
  AND (work streams don't depend on each other)
  AND (time-sensitive OR comparative analysis)
  AND (user hasn't expressed preference for sequential)
THEN spawn in parallel (same turn)
ELSE execute sequentially
```

### Which phase registry should I load?

```
Load ALL phase registries where task touches that phase:
- Contains discovery verbs/artifacts? → Load discovery-phase.md
- Contains design verbs/artifacts? → Load design-phase.md
- Contains implementation verbs/artifacts? → Load implementation-phase.md
- Contains validation verbs/artifacts? → Load validation-phase.md

Most tasks touch multiple phases → Load multiple registries
```

### When should I stop and ask the user?

```
Stop and ask when:
- The recommendation has multiple valid approaches with different tradeoffs
- Validation failed and decision is between iterate/pivot/kill
- Cost is significant (> $1000, > 1 week of time)
- Risk is high (revenue-critical feature, vendor-facing change)
- User preference is needed (aesthetic choice, technical framework)

Don't stop and ask when:
- Next step is obvious and low-risk
- Skill invocation is clearly what was requested
- Decision can be made with available information
```

## Output Format After Orchestration

After sub-skills complete, integrate their outputs into the trio framework:

```
POV Designer
[Use findings from design skills to inform this POV]

POV Developer
[Use findings from implementation skills to inform this POV]

POV Product Manager
[Use findings from discovery/validation skills to inform this POV]

Disagreement
[If skill outputs reveal new tensions, surface them here]

Recommendation
[The call, informed by skill outputs]

Why
[What would change this recommendation—what new information would flip it]

Validation
[Validation skill results OR validation plan if not yet executed]

---

## Sub-Skills Used

- `skill-name-1`: [What it did, link to output]
- `skill-name-2`: [What it did, link to output]

## Next Steps

1. [What should happen next, based on skill outputs]
2. [Any follow-up validation or iteration needed]
3. [Deployment/rollout plan if ready to ship]
```

This format ensures skill outputs are integrated into the trio's reasoning, not just appended as raw data.
