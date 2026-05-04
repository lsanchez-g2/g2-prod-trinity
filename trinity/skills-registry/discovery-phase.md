# Discovery Phase Skills

Skills for research, opportunity framing, competitive analysis, user understanding, and validation planning. Use these when the trio is in discovery mode—before committing to a solution.

## Primary Skills (Invoke automatically when recommended)

### `deep-research` - Comprehensive research and synthesis
**When to use:** Recommendation includes "research", "investigate", "understand", or "explore" + needs depth
**Brand fit:** All brands, especially G2 (enterprise depth) and Software Advice (editorial authority)
**Inputs needed:** Research question, scope, sources to check
**Outputs:** Structured research report with findings, patterns, and recommendations
**Invoke when:** "Research the market for X", "Investigate how competitors handle Y", "Explore user needs around Z"

### `competitive-analysis` - Competitor research and positioning
**When to use:** Recommendation includes "competitive", "competitor", "market position", or "differentiation"
**Brand fit:** All brands
**Inputs needed:** Competitors to analyze, features/surfaces to compare, positioning question
**Outputs:** Competitive matrix, feature gaps, positioning recommendations
**Invoke when:** "Analyze how competitors do X", "What's our competitive position on Y?", "Compare our approach to Z"

### `pm-spec` - Product specification and opportunity framing
**When to use:** Recommendation is "frame the opportunity", "write a spec", or "define the problem"
**Brand fit:** All brands
**Inputs needed:** Problem statement, user needs, success criteria
**Outputs:** Structured product spec with opportunity, assumptions, success metrics
**Invoke when:** "Frame the discovery work", "Write a spec for X", "Define the opportunity"

### `goal-plan` - Goal planning and strategy
**When to use:** Recommendation includes setting goals, defining outcomes, or strategic planning
**Brand fit:** All brands, especially for cross-brand or strategic work
**Inputs needed:** Context, constraints, desired outcomes
**Outputs:** Goal structure, key results, plan
**Invoke when:** "Plan the roadmap for X", "Set goals for Y initiative", "Define success for Z"

## Secondary Skills (Suggest to user if relevant)

### `sparc-methodology` - Structured problem-solving
**When to use:** Complex, multi-stakeholder problems that need rigorous breakdown
**Best for:** Large features, architectural decisions, cross-team initiatives
**Suggest when:** Problem is ambiguous or politically charged

### `design-brief` - Design briefs for creative work
**When to use:** Designer POV recommends "create a brief" or kicking off design work
**Best for:** Marketing pages, landing pages, visual identity work
**Suggest when:** Handing off to design team or agency

### `adr-create` - Architecture Decision Records
**When to use:** Developer POV recommends documenting a technical decision
**Best for:** G2 (enterprise), technical platforms, architectural choices
**Suggest when:** Technical decision with long-term implications

## Brand-Specific Selection Logic

### Capterra (SMB, PPC-driven, scan-first)
**Prioritize speed and validation:**
- Use `deep-research` for quick competitive scans (not exhaustive)
- Use `competitive-analysis` focused on conversion patterns and PPC tactics
- Keep research time-boxed: 2-3 competitors max, focused on category pages and monetization

**Example:**
```
IF brand = Capterra AND task = "research AI category summaries"
  → Invoke `competitive-analysis` with scope: "Check 3 top competitors' category pages, 
     focus on AI-generated content, how it's positioned, and conversion impact"
```

### Software Advice (Advisor-mediated, PPL, editorial)
**Prioritize trust signals and content quality:**
- Use `deep-research` for editorial depth and E-E-A-T signals
- Use `competitive-analysis` focused on advisor models and lead quality
- Research should inform content strategy and advisor positioning

**Example:**
```
IF brand = Software Advice AND task = "research advisor chat features"
  → Invoke `deep-research` with scope: "How do competitors balance human advisors 
     vs AI chat? What do buyers trust? Citation quality? Lead capture rates?"
```

### GetApp (Tech-forward SMB, comparison-driven, EU-leaning)
**Prioritize feature depth and comparison clarity:**
- Use `competitive-analysis` focused on comparison features and filtering
- Research should inform feature taxonomy and comparison tables
- Consider EU privacy/data regulations

### G2 (Enterprise, peer-driven, subscription)
**Prioritize depth, data, and enterprise patterns:**
- Use `deep-research` for exhaustive analysis (not quick scans)
- Use `sparc-methodology` for complex architectural decisions
- Research should inform platform strategy, not just feature tactics

**Example:**
```
IF brand = G2 AND task = "research intent data features"
  → Invoke `deep-research` with scope: "Enterprise buyer behavior, intent signal 
     types, data privacy regulations, vendor expectations, monetization models—full depth"
```

## Parallel Agent Spawning for Discovery

Spawn parallel agents when discovery requires independent research streams:

### Pattern 1: Multi-competitor analysis
```
Task: "Understand how top 5 competitors handle vendor onboarding"
↓
Spawn 5 agents, each with `competitive-analysis`:
  - Agent 1: Competitor A's onboarding flow
  - Agent 2: Competitor B's onboarding flow
  - Agent 3: Competitor C's onboarding flow
  - Agent 4: Competitor D's onboarding flow
  - Agent 5: Competitor E's onboarding flow
↓
Synthesize: Common patterns, unique approaches, gaps
```

### Pattern 2: Multi-source research
```
Task: "Research buyer needs for AI recommendation features"
↓
Spawn 3 agents in parallel:
  - Agent 1: `deep-research` on academic papers and AI research
  - Agent 2: `competitive-analysis` on how competitors do it
  - Agent 3: Internal data analysis (user interviews, support tickets, reviews)
↓
Synthesize: What buyers actually need vs. what competitors offer vs. what research suggests
```

### Pattern 3: Disaggregated POV research
```
Disagreement: Designer wants ethnographic research (slow, deep)
             Developer wants to prototype and instrument (fast, learn by building)
             PM unsure which approach uncovers the real need
↓
Spawn 2 agents in parallel:
  - Agent 1: Designer + `deep-research` on user behavior (3 days)
  - Agent 2: Developer + `web-prototype` + instrument and ship (1 week)
↓
Compare: What did research find vs. what did real usage reveal? Use both.
```

## Selection Decision Tree

```
IF recommendation contains ["research", "investigate", "understand", "explore"]
  AND scope is narrow (1-3 specific questions)
  → Invoke `competitive-analysis` (faster, focused)
  
  AND scope is broad (open-ended, multi-faceted)
  → Invoke `deep-research` (comprehensive)

IF recommendation contains ["spec", "frame", "opportunity", "define problem"]
  → Invoke `pm-spec`

IF recommendation contains ["goal", "strategy", "roadmap", "plan"]
  → Invoke `goal-plan`

IF recommendation contains ["competitors", "competitive", "market position"]
  → Invoke `competitive-analysis`

IF multiple independent research streams identified
  → Spawn parallel agents, each with appropriate skill
```

## Fallback Behavior

If the required skill is not installed:
1. **Notify:** "The `skill-name` skill would be ideal for this. Install it with: `claude skill install skill-name`"
2. **Offer:** "I can do this research inline, but it won't be as structured. Proceed?"
3. **If user agrees:** Execute the research inline using the trio framework
4. **Document:** Note what was done and how the dedicated skill would improve it

## Output Integration

When a discovery skill completes:
1. **Read the output** (research report, competitive analysis, spec)
2. **Feed into trio analysis:** Use findings to inform Designer/Developer/PM POVs
3. **Surface in Disagreement:** If research reveals tension, make it explicit
4. **Update Recommendation:** Recommendation should reference research findings
5. **Refine Validation:** Research often reveals better validation experiments

**Example:**
```
User: "Should we add AI-generated review summaries to Capterra product pages?"

Trio detects: Need competitive analysis
↓
Invoke `competitive-analysis` with scope: "Check how top 3 competitors (G2, TrustRadius, 
  Gartner Peer Insights) display AI review summaries. Focus on: placement, citations, 
  buyer trust signals, vendor concerns."
↓
Analysis returns: "All 3 use summaries BUT with different trust approaches..."
↓
Feed into trio:
  - Designer POV: "Based on competitive analysis, citation links are table stakes..."
  - Developer POV: "Analysis shows batch generation is standard, not per-pageview..."
  - PM POV: "Competitors report 15-20% CTR lift, but vendor trust requires..."
↓
Recommendation: "Yes, launch with [specific approach informed by research]"
```
