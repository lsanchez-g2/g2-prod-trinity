# Validation Phase Skills

Skills for A/B testing, metrics design, performance analysis, and validation experiments. Use these when the trio needs to test assumptions, measure outcomes, or validate that a feature delivers the expected value.

## Primary Skills (Invoke automatically when recommended)

### `performance-analysis` - Performance measurement and optimization
**When to use:** Recommendation includes "measure performance", "page speed", "latency", or "optimize"
**Brand fit:** All brands, especially Capterra (high traffic, PPC conversion sensitive to speed)
**Inputs needed:** Surface to analyze (URL, code), performance targets, bottleneck hypotheses
**Outputs:** Performance report, bottleneck identification, optimization recommendations, benchmarks
**Invoke when:** "Measure performance of X", "Optimize Y load time", "Analyze Z latency"

### `verification-quality-assurance` - Quality assurance and testing
**When to use:** Recommendation includes "test the feature", "QA", or "verify functionality"
**Brand fit:** All brands
**Inputs needed:** Feature to test, test scenarios, acceptance criteria, edge cases
**Outputs:** Test results, bug reports, quality assessment
**Invoke when:** "Test the X feature", "QA the Y implementation", "Verify Z works correctly"

### `browser-test` - Cross-browser and device testing
**When to use:** Recommendation includes "test across browsers", "device testing", or "compatibility"
**Brand fit:** All brands (especially mobile-sensitive: Capterra, GetApp)
**Inputs needed:** URLs to test, browsers/devices to cover, test scenarios
**Outputs:** Compatibility report, browser-specific issues, device-specific issues
**Invoke when:** "Test X across browsers", "Verify Y works on mobile", "Check Z compatibility"

## Secondary Skills (Suggest to user if relevant)

### `cost-optimize` - Cost analysis and optimization
**When to use:** PM POV recommends "analyze costs" or feature involves expensive infrastructure (AI, data processing)
**Best for:** AI features (model costs), data pipelines, infrastructure decisions
**Suggest when:** Cost is a concern or recommendation involves expensive operations

### `cost-report` - Cost reporting and tracking
**When to use:** Need to track costs over time or report on infrastructure spending
**Suggest when:** Ongoing cost monitoring needed

### `seo-audit` - SEO audit and recommendations
**When to use:** Recommendation involves SEO validation or organic search impact
**Best for:** Capterra (SEO-critical), Software Advice (editorial authority), content-heavy features
**Suggest when:** Feature touches category pages, content, URLs, or schema markup

### `security-scan` / `security-audit` - Security validation
**When to use:** Security validation needed post-implementation
**Suggest when:** Feature involves PII, payment data, or vendor access

### `deep-research` - Post-launch research
**When to use:** Validation requires understanding user behavior or market response
**Suggest when:** Need to research how users actually use the feature

## Brand-Specific Selection Logic

### Capterra (SMB, PPC-driven, conversion-sensitive, SEO-critical)
**Validation priorities:**
- **PPC conversion impact** - Does the feature increase/decrease "Visit Website" clicks?
- **Page speed** - Performance directly affects PPC conversion and SEO ranking
- **SEO impact** - Organic search drives traffic; any degradation is costly
- **Lead quality** - For vendor-side changes, does it affect vendor satisfaction or churn?

**Skill selection:**
```
IF brand = Capterra AND feature = category page change
  → Invoke `performance-analysis` (page speed is conversion)
  → Invoke `seo-audit` (organic search is traffic source)
  → Suggest: A/B test with "time-to-first-product-click" as primary metric

IF brand = Capterra AND feature = PPC button/CTA change
  → Validation: A/B test with "PPC CTR" as primary metric
  → Track: Revenue per visitor, vendor satisfaction, lead quality
  → Decision rule: "If PPC CTR ↑5%+ AND vendor quality holds → ship to 100%"

IF brand = Capterra AND feature = AI-generated content
  → Invoke `seo-audit` (AI content may affect SEO)
  → Invoke `cost-optimize` (model costs at 5.1M visits/month)
  → Validation: A/B test on 50 categories, watch organic ranking + PPC conversion
```

**Key metrics by surface:**
- **Category pages:** Time-to-first-click, PPC CTR, bounce rate, organic ranking
- **Product profiles:** Review submission rate, "Visit Website" CTR, profile completeness
- **Comparison:** Products compared per session, time on page, PPC CTR
- **Search:** Click-through from search, query refinement rate, zero-result rate

### Software Advice (Advisor-mediated, PPL, form-driven, trust-sensitive)
**Validation priorities:**
- **Form fill rate** - Does the feature increase/decrease advisor contact forms?
- **Lead quality** - Does it affect qualification depth or vendor satisfaction?
- **Advisor trust** - Do buyers still perceive advisors as neutral and helpful?
- **Editorial authority** - Does it enhance or undermine trust signals?

**Skill selection:**
```
IF brand = Software Advice AND feature = advisor contact form change
  → Validation: A/B test with "form fill rate" AND "lead quality" as dual metrics
  → Track: Vendor dispute rate, vendor satisfaction, advisor conversion rate
  → Decision rule: "If form fills ↑10%+ AND dispute rate ↓5% → ship"

IF brand = Software Advice AND feature = AI advisor chat
  → Invoke `deep-research` (how do buyers perceive AI vs human advisors?)
  → Validation: Qualitative research (user interviews) + A/B test
  → Track: Form fill rate, advisor engagement rate, lead quality, buyer trust signals

IF brand = Software Advice AND feature = editorial content change
  → Invoke `seo-audit` (editorial is SEO spine)
  → Validation: Organic ranking, time on page, form fill rate from content pages
```

**Key metrics by surface:**
- **Category/buyer guide pages:** Form fill rate, time on page, scroll depth, organic ranking
- **Product profiles:** Form fill rate, advisor engagement rate, review read rate
- **Advisor surfaces:** Lead qualification depth, advisor satisfaction, conversion rate
- **Forms:** Completion rate, field-level drop-off, qualification quality, vendor disputes

### GetApp (Tech-forward SMB, comparison-driven, filter-heavy, EU-leaning)
**Validation priorities:**
- **Comparison usage** - Does the feature improve product comparison and filtering?
- **Feature clarity** - Do tech buyers understand the feature taxonomy?
- **Mobile experience** - Tech buyers expect mobile parity
- **EU compliance** - GDPR, privacy, data handling must be validated

**Skill selection:**
```
IF brand = GetApp AND feature = comparison/filtering change
  → Validation: A/B test with "products compared per session" as primary metric
  → Track: Filter usage, comparison saves, PPC CTR, time-to-decision

IF brand = GetApp AND feature = EU user data
  → Invoke `security-scan` (GDPR compliance validation)
  → Validation: Privacy review, data retention audit, consent flow testing
  → Track: EU user trust signals, data export requests, deletion requests
```

**Key metrics by surface:**
- **Category pages:** Filter usage, products compared, PPC CTR, mobile vs desktop usage
- **Comparison pages:** Comparison depth (# products), feature expansion rate, save/share usage
- **Product profiles:** Technical detail engagement, review read depth, integration interest

### G2 (Enterprise, subscription, data-rich, intent-driven)
**Validation priorities:**
- **Data accuracy** - Intent signals, Grid placement, review scores must be precise
- **Enterprise reliability** - Downtime or bugs are unacceptable
- **Vendor value** - Does the feature drive subscription retention or upsell?
- **Integration quality** - CRM integrations must be reliable and accurate

**Skill selection:**
```
IF brand = G2 AND feature = intent data change
  → Validation: Accuracy validation (false positive rate, false negative rate)
  → Track: Vendor usage, conversion from intent signal, vendor NPS
  → Decision rule: "If accuracy >95% AND vendor satisfaction ↑ → ship"

IF brand = G2 AND feature = Grid algorithm change
  → Validation: Backtest against historical data, vendor communication
  → Track: Grid position changes, vendor complaints, buyer trust signals
  → Rollout: Announce changes, give vendors time to adjust, monitor closely

IF brand = G2 AND feature = CRM integration
  → Invoke `verification-quality-assurance` (integration testing)
  → Validation: Test all error cases, rate limits, data sync accuracy
  → Track: Integration adoption, error rates, vendor support tickets

IF brand = G2 AND feature = AI-powered feature
  → Invoke `cost-optimize` (enterprise scale + AI costs)
  → Validation: Model accuracy, latency, cost per query, user satisfaction
  → Track: Usage volume, cost trends, accuracy over time
```

**Key metrics by surface:**
- **Grid/category pages:** Grid position accuracy, vendor satisfaction, buyer trust signals
- **Intent data:** Signal accuracy, false positive rate, vendor conversion rate
- **Vendor dashboard:** Engagement rate, feature adoption, NPS, churn indicators
- **Integrations:** Success rate, error rate, data sync accuracy, support tickets

## Validation Strategy by Feature Type

### New features (first time shipping)
**Validation approach:**
1. **Smallest viable test** - Test on smallest population that gives statistical significance
2. **Instrumentation first** - Metrics must be in place BEFORE launch
3. **Qualitative + quantitative** - Numbers + user feedback
4. **Decision rule upfront** - "If X metric moves Y%, then Z action"

**Example validation plan:**
```
Feature: AI category summary on Capterra
Riskiest assumption: Buyers will trust AI-generated content and it will reduce time-to-click

Validation:
- A/B test on 50 mid-sized categories (20K visitors/month)
- Duration: 2 weeks
- Primary metric: Time-to-first-product-click (target: ↓10%+)
- Secondary metrics: PPC CTR, bounce rate, organic ranking
- Qualitative: User interviews with 10 buyers who saw summaries
- Decision rule: 
  IF time-to-click ↓10%+ AND PPC CTR holds AND organic ranking holds
  THEN expand to 200 categories
  ELSE iterate or kill
```

### Changes to existing features (improvements)
**Validation approach:**
1. **Regression testing** - Ensure existing functionality doesn't break
2. **A/B test** - Compare new vs old
3. **Monitoring** - Watch key metrics closely post-launch
4. **Rollback plan** - Be ready to revert quickly

### Revenue-critical features (PPC buttons, forms, payment flows)
**Validation approach:**
1. **Canary deployment** - Ship to 1% of traffic first
2. **Real-time monitoring** - Watch revenue metrics minute-by-minute
3. **Auto-rollback** - Revert automatically if key metric drops >5%
4. **Vendor communication** - Warn vendors of changes that affect them

### AI/ML features (recommendations, summaries, predictions)
**Validation approach:**
1. **Offline evaluation** - Test on historical data first (precision, recall, accuracy)
2. **Human eval** - Have humans grade a sample of outputs (e.g., 100 summaries)
3. **Gradual rollout** - 1% → 10% → 50% → 100%, watching quality
4. **Cost monitoring** - AI can get expensive at scale; track cost per query
5. **Feedback loop** - Collect user corrections to improve the model

**Invoke `cost-optimize` for AI features to model costs at scale before launch.**

## Parallel Agent Spawning for Validation

Spawn parallel agents when validation requires multiple independent tests:

### Pattern 1: Multi-metric validation
```
Task: "Validate the AI category summary feature"

↓ Spawn 4 agents in parallel:
  - Agent 1: `performance-analysis` - Measure page speed impact
  - Agent 2: `seo-audit` - Check organic ranking impact
  - Agent 3: `cost-optimize` - Model AI costs at full scale
  - Agent 4: `deep-research` - User interviews (qualitative)
↓
Synthesize: Combine quantitative (speed, SEO, cost) + qualitative (trust, usefulness) → decision
```

### Pattern 2: Cross-browser + performance
```
Task: "Validate new comparison page design"

↓ Spawn 2 agents in parallel:
  - Agent 1: `browser-test` - Test across browsers and devices
  - Agent 2: `performance-analysis` - Measure load time and interactions
↓
Synthesize: Browser issues + performance bottlenecks → fix → retest
```

### Pattern 3: Security + cost validation
```
Task: "Validate new API endpoint before launch"

↓ Spawn 3 agents in parallel:
  - Agent 1: `security-scan` - Security validation
  - Agent 2: `performance-analysis` - Load testing, rate limits
  - Agent 3: `cost-optimize` - Infrastructure cost at scale
↓
Synthesize: Security cleared + performance acceptable + cost justified → ship
```

## Selection Decision Tree

```
IF recommendation contains ["validate", "test", "measure", "check"]
  AND performance/speed/latency mentioned
    → Invoke `performance-analysis`
  
  AND cross-browser/device mentioned
    → Invoke `browser-test`
  
  AND quality/functionality mentioned
    → Invoke `verification-quality-assurance`
  
  AND SEO/organic search mentioned
    → Suggest `seo-audit`
  
  AND cost/infrastructure mentioned
    → Suggest `cost-optimize`
  
  AND security/compliance mentioned
    → Suggest `security-scan`

IF recommendation includes A/B test or experimentation
  → Provide A/B test plan inline (or suggest dedicated skill if available)
  → Include: Hypothesis, population, duration, metrics, decision rule

IF recommendation includes qualitative research
  → Suggest `deep-research` for user interviews or behavioral research
```

## Fallback Behavior

If the required skill is not installed:
1. **Notify:** "The `skill-name` skill would provide structured validation. Install: `claude skill install skill-name`"
2. **Offer:** "I can provide a validation plan inline. Proceed?"
3. **If user agrees:** Write validation plan with metrics, test approach, decision rules
4. **Note limitations:** "With `performance-analysis` installed, this would include automated benchmarking and bottleneck identification."

## Output Integration

When a validation skill completes:
1. **Review the results** (performance report, test results, audit findings)
2. **Compare to success criteria:** Did it meet the target? Pass the threshold?
3. **Surface in Recommendation:** Update the trio's recommendation based on validation results
4. **Decision point:** Ship, iterate, or kill?
   - **Ship:** Validation passed, expand rollout
   - **Iterate:** Close but not quite, make changes and retest
   - **Kill:** Hypothesis disproven, abandon or rethink
5. **Document learnings:** What did we learn? What would we do differently next time?

**Example:**
```
User: "Validate the AI category summary feature for Capterra"

Trio provided validation plan:
  - A/B test on 50 categories, 2 weeks
  - Metrics: Time-to-first-click (↓10%+), PPC CTR (hold), bounce rate (hold)
  - Instrumentation in place
↓
Spawn 3 agents in parallel:
  - Agent 1: `performance-analysis` - Measure page speed impact
  - Agent 2: `seo-audit` - Monitor organic ranking
  - Agent 3: `cost-optimize` - Calculate AI costs at 900-2000 categories
↓
Results after 2 weeks:
  - Performance: Page speed ↓150ms (good)
  - SEO: Organic ranking holds (no negative impact)
  - Cost: $2.50/category/month at scale = $2,250-$5,000/month (acceptable)
  - A/B test: Time-to-click ↓14%, PPC CTR +2%, bounce rate -3% (WIN!)
  - Qualitative: 8/10 users found summaries helpful, wanted citations (already have them)
↓
Trio updates recommendation:
  POV Designer: "Validation confirms trust signals work—keep citation links"
  POV Developer: "Performance acceptable, costs justified by conversion lift"
  POV PM: "Clear win: ↓14% time-to-click translates to ~15K more PPC clicks/month 
           at 5.1M visits. ROI is 5-10x the AI costs. Ship to all categories."
↓
Decision: SHIP to all 900-2000 categories, monitor for 30 days, iterate on edge cases
```

## Validation Best Practices

### Always define success criteria upfront
Before testing, agree on:
- **Primary metric:** The one that matters most (e.g., "form fill rate")
- **Secondary metrics:** Supporting signals (e.g., "lead quality", "page speed")
- **Guardrail metrics:** Things that must not break (e.g., "vendor satisfaction", "organic ranking")
- **Decision rule:** "If X, then Y" (e.g., "If form fills ↑10%+ AND disputes ↓5%, then ship")

### Test the riskiest assumption first
If the feature relies on multiple assumptions, test the scariest one first:
- "Will buyers trust AI-generated content?" → Test with prototype + user interviews
- "Will advisors adopt this tool?" → Test with 5 advisors before building for 100

### Keep validation cheap and fast
The best validation is the one that teaches the most for the least cost and time:
- **Prototype + 10 user interviews** beats **3-month build + no validation**
- **A/B test on 5% of traffic for 1 week** beats **ship to 100% and hope**
- **Offline eval on historical data** beats **ship and learn from production errors**

### Know when to kill
Sunk cost fallacy is real. If validation disproves the hypothesis, kill the feature:
- "We spent 6 weeks building this" is not a reason to ship
- "But we announced it" is not a reason to ship
- "Maybe it'll work on a different brand?" is usually wishful thinking

Better to kill and redirect effort than to ship something that doesn't work.
