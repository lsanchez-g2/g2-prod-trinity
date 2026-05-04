# Design Phase Skills

Skills for wireframing, prototyping, design systems, UI/UX work, and visual design. Use these when the trio moves from "what to build" to "how it looks and behaves."

## Primary Skills (Invoke automatically when recommended)

### `frontend-design` - Full design implementation with code
**When to use:** Recommendation includes "implement", "build", "code" + design work
**Brand fit:** All brands
**Inputs needed:** Design requirements, component list, brand guidelines, target framework
**Outputs:** Production-ready HTML/CSS/JS with design system integration
**Invoke when:** "Build the X feature", "Implement the Y component", "Code the Z page"
**Note:** This is BOTH a design skill AND an implementation skill—it produces working code, not just mockups

### `wireframe-sketch` - Low-fidelity wireframes and flows
**When to use:** Recommendation includes "wireframe", "sketch", or early exploration phase
**Brand fit:** All brands, especially fast-moving SMB contexts (Capterra, Software Advice, GetApp)
**Inputs needed:** User flow, key screens, interaction notes, must-have elements
**Outputs:** ASCII/text wireframes, interaction notes, state diagrams
**Invoke when:** "Wireframe the X flow", "Sketch the Y interface", "Map out the Z journey"
**Best for:** Early validation, stakeholder alignment, before investing in high-fidelity

### `web-prototype` - Interactive web prototypes
**When to use:** Recommendation includes "prototype" without specifying fidelity
**Brand fit:** All brands
**Inputs needed:** Design specs, interaction patterns, content, brand assets
**Outputs:** HTML/CSS/JS interactive prototype
**Invoke when:** "Prototype the X feature", "Build a clickable demo of Y"

### `web-prototype-taste-*` - High-fidelity brand-aware prototypes
**When to use:** Recommendation specifies visual quality, brand alignment, or production-ready design
**Brand fit:** Context-specific (see below)
**Variants:**
- `web-prototype-taste-brutalist` → Capterra (fast, conversion-focused, scan-first, clear CTAs)
- `web-prototype-taste-editorial` → Software Advice (trust, authority, editorial quality)
- `web-prototype-taste-soft` → G2 (enterprise polish, data-rich, professional)

**Invoke when:** "Prototype X with Capterra's fast-scan aesthetic", "Build an editorial-quality Y for Software Advice"

### `mobile-app` - Mobile app design and prototyping
**When to use:** Recommendation includes "mobile", "iOS", "Android", or mobile-first
**Brand fit:** All brands, especially GetApp (tech-forward) and G2 (enterprise mobile)
**Inputs needed:** Mobile-specific requirements, platform (iOS/Android/both), interactions
**Outputs:** Mobile prototype or production code
**Invoke when:** "Design the mobile X", "Prototype the app for Y"

### `ui-ux-pro-max` - Advanced UX patterns and interactions
**When to use:** Recommendation includes complex interactions, accessibility deep-dive, or UX research
**Brand fit:** G2 (enterprise complexity), any brand with accessibility requirements
**Inputs needed:** Interaction requirements, accessibility standards (WCAG level), user research
**Outputs:** Detailed UX patterns, interaction specs, accessibility audit
**Invoke when:** "Design complex filtering for X", "Ensure Y meets WCAG 2.2 AA", "Deep UX analysis of Z"

## Secondary Skills (Suggest to user if relevant)

### `design-md` - Design documentation in markdown
**When to use:** Designer POV recommends documenting design decisions
**Best for:** Design systems, component libraries, pattern documentation
**Suggest when:** Building or updating design system

### `ckm-design-system` - Design system creation and management
**When to use:** Recommendation includes "design system", "component library", or "design tokens"
**Best for:** Cross-brand work, platform-level decisions
**Suggest when:** Designing reusable component systems

### `dashboard` - Dashboard design for metrics and data
**When to use:** Recommendation includes "dashboard", "metrics", "analytics", "data visualization"
**Best for:** Vendor dashboards, internal tools, reporting surfaces
**Suggest when:** Designing data-heavy interfaces

### `taste-design` - High-quality design patterns
**When to use:** Ambiguous visual quality requirement
**Suggest when:** User wants "make it beautiful" without specific brand context

### `design-brief` - Design briefs for handoff
**When to use:** Handing off to external designers or agencies
**Suggest when:** Need to brief a design team

### Figma MCP tools - Direct Figma integration
**When to use:** Design already exists in Figma or team works in Figma
**Tools:** `get_design_context`, `use_figma`, `upload_assets`
**Suggest when:** User provides Figma URL or mentions existing designs

## Brand-Specific Selection Logic

### Capterra (SMB, PPC-driven, scan-first, conversion-focused)
**Design priorities:**
- **Speed over polish** - Fast-loading, immediate comprehension
- **Conversion-optimized** - Clear CTAs, blue "Visit Website" buttons prominent
- **Scan-friendly** - Information hierarchy for skimmers
- **Trust signals** - Badges, reviews, ratings visible immediately

**Skill selection:**
```
IF brand = Capterra AND task = "prototype category page"
  → Invoke `web-prototype-taste-brutalist`
  → Focus on: Fast load, clear PPC button placement, trust signals, mobile-first

IF brand = Capterra AND task = "wireframe comparison feature"
  → Invoke `wireframe-sketch`
  → Focus on: Side-by-side clarity, CTA visibility, mobile collapse patterns
```

**Avoid:**
- Long editorial content above the fold
- Subtle micro-interactions that slow perception
- Enterprise complexity in SMB surfaces

### Software Advice (Advisor-mediated, PPL, editorial, trust-driven)
**Design priorities:**
- **Trust and authority** - Editorial polish, expert credibility signals
- **Form optimization** - Advisor contact forms are the conversion point
- **Content hierarchy** - Buyer guides and educational content prominent
- **Conversation cues** - Human advisor presence, chat affordances

**Skill selection:**
```
IF brand = Software Advice AND task = "prototype buyer guide page"
  → Invoke `web-prototype-taste-editorial`
  → Focus on: Editorial layout, expert bylines, form placement, trust signals

IF brand = Software Advice AND task = "design advisor chat interface"
  → Invoke `ui-ux-pro-max`
  → Focus on: Human vs AI indicators, conversation flow, lead capture, reassurance
```

**Avoid:**
- Purely self-serve experiences (goes against advisor model)
- PPC-style aggressive CTAs (wrong monetization model)
- Content-light pages (editorial is the asset)

### GetApp (Tech-forward SMB, comparison-driven, EU-leaning)
**Design priorities:**
- **Comparison clarity** - Feature matrices, side-by-side views
- **Technical depth** - More detail than Capterra, less than G2
- **Filter-heavy** - Category pages with robust filtering
- **EU data sensibility** - Privacy-forward, GDPR-aware patterns

**Skill selection:**
```
IF brand = GetApp AND task = "prototype comparison page"
  → Invoke `web-prototype`
  → Focus on: Feature matrix clarity, filter sidebar, technical detail depth

IF brand = GetApp AND task = "design category filtering"
  → Invoke `ui-ux-pro-max`
  → Focus on: Complex filter interactions, save/share state, mobile patterns
```

### G2 (Enterprise, peer-driven, subscription, data-rich)
**Design priorities:**
- **Enterprise polish** - Professional, sophisticated, data-dense
- **Peer signals** - Review badges, Grid placement, social proof
- **Data visualization** - Charts, trends, intent signals
- **Integration depth** - CRM integrations, API access, technical surfaces

**Skill selection:**
```
IF brand = G2 AND task = "prototype Grid category page"
  → Invoke `web-prototype-taste-soft`
  → Focus on: Data density, Grid visualization, peer review prominence, professional polish

IF brand = G2 AND task = "design vendor dashboard metrics"
  → Invoke `dashboard`
  → Focus on: Data visualization, trend charts, intent signals, export capabilities
```

**Avoid:**
- SMB simplicity (enterprise buyers expect depth)
- Consumer-style aesthetics
- Hiding data behind too many clicks

## Parallel Agent Spawning for Design

Spawn parallel agents when design requires exploration of multiple directions:

### Pattern 1: Design variants exploration
```
Disagreement: Designer wants minimal (trust, clarity)
             Developer wants feature-rich (show capabilities)
             PM wants data-driven decision

↓ Spawn 3 agents in parallel:
  - Agent 1: `web-prototype-taste-brutalist` - Minimal variant
  - Agent 2: `web-prototype` - Feature-rich variant
  - Agent 3: `competitive-analysis` - What converts best in category?
↓
Synthesize: Build both, A/B test with conversion data, decide based on results
```

### Pattern 2: Multi-platform design
```
Task: "Design the review submission flow for mobile and desktop"

↓ Spawn 2 agents in parallel:
  - Agent 1: `mobile-app` - Mobile-first design
  - Agent 2: `web-prototype` - Desktop design
↓
Synthesize: Ensure consistent flow across platforms, optimize for each context
```

### Pattern 3: Accessibility audit + redesign
```
Task: "Ensure the vendor dashboard meets WCAG 2.2 AA"

↓ Spawn 2 agents in parallel:
  - Agent 1: `ui-ux-pro-max` - Accessibility audit (identify issues)
  - Agent 2: `dashboard` - Begin redesign of dashboard structure
↓
Agent 1 completes first → feed findings into Agent 2's ongoing redesign
```

## Selection Decision Tree

```
IF recommendation contains ["wireframe", "sketch", "map out", "rough"]
  AND stage = early exploration
  → Invoke `wireframe-sketch`

IF recommendation contains ["prototype", "build", "design"]
  AND specifies brand aesthetic
    IF brand = Capterra → `web-prototype-taste-brutalist`
    IF brand = Software Advice → `web-prototype-taste-editorial`
    IF brand = G2 → `web-prototype-taste-soft`
    IF brand = GetApp → `web-prototype` (generic)
  
  AND mobile-specific
    → Invoke `mobile-app`
  
  AND data/dashboard
    → Invoke `dashboard`
  
  AND complex UX/accessibility
    → Invoke `ui-ux-pro-max`
  
  AND generic/no brand context
    → Invoke `web-prototype`

IF recommendation contains ["implement", "code", "production"]
  AND design + code needed
  → Invoke `frontend-design`

IF recommendation contains ["design system", "component library"]
  → Suggest `ckm-design-system`

IF user provides Figma URL
  → Suggest Figma MCP tools
```

## Fallback Behavior

If the required skill is not installed:
1. **Notify:** "The `skill-name` skill would be ideal here. Install: `claude skill install skill-name`"
2. **Offer:** "I can design this inline with HTML/CSS, but without the specialized brand patterns. Proceed?"
3. **If user agrees:** Build inline using basic web technologies
4. **Note limitations:** "With `web-prototype-taste-brutalist` installed, this would match Capterra's conversion-optimized aesthetic automatically."

## Output Integration

When a design skill completes:
1. **Review the output** (wireframes, prototype, code)
2. **Validate against POVs:**
   - Designer: Does it match UX principles and brand guidelines?
   - Developer: Is it implementable? Any technical debt?
   - PM: Does it serve the user need and business goal?
3. **Surface gaps in Disagreement:** If the design reveals new tensions, make them explicit
4. **Update Validation:** Design prototypes often reveal new assumptions to test
5. **Provide next steps:** "Test this with 10 users" or "Deploy to staging for team review"

**Example:**
```
User: "Design the AI category summary feature for Capterra"

Trio recommendation: "Prototype with brutalist aesthetic, focus on scan-first, 
  trust signals, and mobile-first"
↓
Invoke `web-prototype-taste-brutalist` with:
  - Content: AI-generated category summary
  - Trust signals: Citation links, "Generated by AI" label
  - Mobile-first: Summary expands on tap, doesn't block product listings
  - CTAs: Blue "Visit Website" buttons remain prominent
↓
Prototype returns: HTML/CSS/JS with Capterra aesthetic
↓
Trio validates:
  - Designer: "Good - scan-friendly, trust signals present, mobile works"
  - Developer: "Can implement - batch generation compatible, SEO markup clean"
  - PM: "Test assumption: Does summary reduce time-to-click by 10%+? A/B test needed"
↓
Output to user: "Here's the prototype [link]. Next: A/B test on 50 categories, 
  measure time-to-first-product-click."
```
