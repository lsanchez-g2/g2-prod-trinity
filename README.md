# 🎯 Product Trio

> **Transform Claude into your senior product team** — Designer, Developer, and Product Manager working together on every decision, now with **intelligent sub-skill orchestration**.

<p align="center">
  <img src="product-trio-hero.jpg" alt="Product Trio - Three perspectives, one decision" width="100%">
</p>

<p align="center">
  <a href="https://github.com/lsanchez-g2/g2-prod-trinity/releases"><img src="https://img.shields.io/github/v/release/lsanchez-g2/g2-prod-trinity?style=flat-square" alt="Latest Release"></a>
  <a href="#installation"><img src="https://img.shields.io/badge/claude-skill-purple?style=flat-square" alt="Claude Skill"></a>
  <a href="#license"><img src="https://img.shields.io/badge/license-MIT-blue?style=flat-square" alt="License"></a>
  <a href="#intelligent-orchestration"><img src="https://img.shields.io/badge/orchestration-intelligent-green?style=flat-square" alt="Intelligent Orchestration"></a>
</p>

---

## 🌟 What is Product Trio?

Product Trio is a **Claude Code skill** that gives you **three expert perspectives** on every product decision, backed by **intelligent sub-skill orchestration** that automatically selects and coordinates specialized skills based on your brand context, task phase, and output needs.

Instead of one-dimensional answers, you get:
- 🎨 **Designer POV** — User experience, accessibility, trust signals
- 💻 **Developer POV** — Technical feasibility, scalability, implementation complexity
- 📊 **PM POV** — Business outcomes, metrics, opportunity cost, validation strategy
- ⚡ **Mandatory Disagreement** — Real tradeoffs surfaced explicitly
- 🤖 **Intelligent Orchestration** — Automatic coordination of 50+ specialized skills

**Built specifically for the G2 ecosystem**: Capterra, Software Advice, GetApp, and G2.

---

## 🚀 What's New: Intelligent Orchestration

The latest version includes a **context-aware skill orchestration system** that automatically:

### 🎯 Selects the Right Skills
Based on:
- **Task phase** (Discovery → Design → Implementation → Validation)
- **Brand context** (Capterra's PPC focus vs Software Advice's PPL model)
- **Output artifact** (Research report vs Wireframe vs Production code)
- **Feature type** (Revenue-critical vs SEO-critical vs PII-handling)

### 🔄 Coordinates Parallel Work
Spawns multiple agents simultaneously for independent tasks:
```
User: "Build the AI category summary feature for Capterra"

Trio orchestrates:
  ├─ Agent 1: Design (web-prototype-taste-brutalist)
  ├─ Agent 2: Implementation (tdd-workflow)
  └─ Agent 3: Competitive Analysis (competitive-analysis)
       ↓
  Synthesize → Integrated Recommendation
```

### 🧠 Adapts to Your Brand
Different skills for different contexts:

| Brand | Design Style | Revenue Model | Validation Focus |
|-------|-------------|---------------|------------------|
| **Capterra** | Conversion-optimized, scan-first | PPC on "Visit Website" buttons | PPC CTR + Page Speed |
| **Software Advice** | Editorial, trust-driven | PPL on advisor contact forms | Form Fill Rate + Lead Quality |
| **GetApp** | Tech-forward, comparison-heavy | PPC, EU-focused | Comparison Usage + Mobile |
| **G2** | Enterprise polish, data-rich | Subscription + Intent Data | Data Accuracy + Vendor Value |

### 📚 50+ Curated Skills
Organized by phase with automatic selection:

**Discovery Phase:**
- `deep-research`, `competitive-analysis`, `pm-spec`, `goal-plan`

**Design Phase:**
- `frontend-design`, `wireframe-sketch`, `web-prototype-taste-*`, `mobile-app`, `ui-ux-pro-max`

**Implementation Phase:**
- `tdd-workflow`, `api-docs`, `security-audit`, `finishing-a-development-branch`

**Validation Phase:**
- `performance-analysis`, `verification-quality-assurance`, `browser-test`

---

## ✨ Why You'll Love It

### Three-Lens Analysis
Every decision gets examined from three expert viewpoints:

```
POV Designer
Mobile-first layout with trust signals. Citations must be visible 
above the fold. Consider WCAG 2.2 AA for accessibility.

POV Developer  
Batch generation (not per-pageview) scales to 900-2000 categories.
Cost: $2.50/category/month. Cache 24h, fallback for edge cases.

POV Product Manager
Goal: ↓10% time-to-first-click. A/B test 50 categories for 2 weeks.
Track: PPC CTR, bounce rate, organic ranking.

Disagreement
Designer wants comprehensive citations (trust), Developer warns 
this adds complexity (latency), PM wants MVP launch (speed to learn).

Recommendation
Launch with top-3 product citations, batch generation, 95%+ accuracy 
threshold. Phased rollout: 50 → 200 → all categories.

Validation
A/B test on 50 mid-sized categories. If time-to-click ↓10%+ AND 
lead quality holds → expand. Otherwise iterate or kill.
```

### Intelligent Orchestration
The skill automatically:
- ✅ Detects which phase you're in (Discovery/Design/Implementation/Validation)
- ✅ Loads brand-specific context (PPC model, PPL model, etc.)
- ✅ Selects appropriate sub-skills from 50+ curated options
- ✅ Invokes skills automatically when the artifact is clearly needed
- ✅ Spawns parallel agents for independent work streams
- ✅ Integrates outputs back into the trio framework

### Brand-Aware Decisions
Automatically adjusts recommendations based on brand:
- **Capterra**: Fast-scan, conversion-optimized, SEO-critical
- **Software Advice**: Trust signals, advisor positioning, form optimization
- **GetApp**: Technical depth, comparison-driven, EU compliance
- **G2**: Enterprise polish, data accuracy, integration depth

---

## 📦 Installation

### Quick Start (Recommended)

1. **Download the latest release**
   ```bash
   curl -L https://github.com/lsanchez-g2/g2-prod-trinity/releases/latest/download/product-trio.skill -o product-trio.skill
   ```

2. **Install the skill**
   ```bash
   claude skill install product-trio.skill
   ```

3. **Start using it** — The skill activates automatically!

### From Source

```bash
# Clone the repository
git clone https://github.com/lsanchez-g2/g2-prod-trinity.git
cd g2-prod-trinity

# Install directly from source
claude skill install trinity/
```

### Verify Installation

```bash
claude skill list | grep product-trio
```

---

## 🎓 How to Use

The skill **activates automatically** when you work on product decisions. Just describe what you're working on:

### Example 1: Simple Question

**You ask:**
```
Should we add AI-generated category summaries to Capterra?
```

**Trio responds with:**
```
POV Designer → POV Developer → POV Product Manager
     ↓              ↓               ↓
  Disagreement → Recommendation → Validation Plan

Auto-invokes: competitive-analysis (checks 3 competitors)
Result: "Yes, launch with phased rollout..."
```

### Example 2: Build Request

**You ask:**
```
Build the vendor review response widget for GetApp
```

**Trio orchestrates:**
```
Discovery Phase:
  └─ deep-research (vendor needs analysis)
      ↓
Design Phase:
  └─ dashboard (data visualization widget)
      ↓
Implementation Phase (parallel):
  ├─ frontend-design (React component)
  └─ tdd-workflow (backend API + tests)
      ↓
Validation Phase:
  ├─ performance-analysis (load time check)
  └─ browser-test (cross-browser compatibility)
      ↓
Result: Production-ready widget with tests + validation
```

### Example 3: Complex Decision

**You ask:**
```
We're divided on advisor matching for Software Advice. 
Designer wants research, Developer wants to prototype, 
PM wants competitive analysis. Help decide.
```

**Trio orchestrates parallel exploration:**
```
Spawn 3 agents simultaneously:
  ├─ Agent 1: deep-research (ethnographic study)
  ├─ Agent 2: web-prototype (instrumented prototype)
  └─ Agent 3: competitive-analysis + interviews
      ↓
All complete in parallel → Synthesize findings → 
Converged recommendation from all three approaches
```

---

## 🏗️ Architecture

### Orchestration System

```
User Question
     ↓
Phase Detection (Discovery/Design/Implementation/Validation)
     ↓
Load Registries (brand context + skill catalogs)
     ↓
Trio Analysis (Designer + Developer + PM)
     ↓
Skill Selection (context-aware, brand-specific)
     ↓
Execution Strategy (parallel vs sequential)
     ↓
     ├─ Automatic Invocation (primary skills)
     ├─ User Suggestion (secondary skills)
     └─ Parallel Agents (independent work)
     ↓
Output Integration (feed results into trio POVs)
     ↓
Structured Response (POVs → Disagreement → Recommendation → Validation)
```

### Skills Registry

```
trinity/
├── SKILL.md                        # Core trio logic + orchestration
├── brands/                         # Platform-specific context
│   ├── capterra.md                # PPC model, premium profiles, surfaces
│   ├── software-advice.md         # PPL model, advisor mechanics, forms
│   ├── getapp.md                  # Comparison-driven, EU focus
│   └── g2.md                      # Enterprise, intent data, integrations
├── lenses/                         # Experience perspectives
│   ├── buyer-experience.md        # Search, category pages, discovery
│   └── vendor-experience.md       # Dashboard, profiles, lead delivery
├── references/                     # Deep heuristics
│   ├── pov-designer.md            # UX principles, accessibility, trust
│   ├── pov-developer.md           # Feasibility, architecture, AI/ML
│   ├── pov-pm.md                  # Discovery, metrics, validation
│   └── disagreement-patterns.md   # How to force productive tension
└── skills-registry/               # 🆕 Intelligent orchestration
    ├── discovery-phase.md         # Research & competitive analysis
    ├── design-phase.md            # Wireframes, prototypes, UI/UX
    ├── implementation-phase.md    # Coding, testing, APIs, security
    ├── validation-phase.md        # A/B testing, metrics, performance
    ├── orchestration-rules.md     # Meta-logic for coordination
    └── examples.md                # 5 detailed orchestration examples
```

---

## 🎯 Real-World Examples

### Example 1: Revenue-Critical Feature
> "Add AI category summaries to Capterra category pages"

**Trio automatically:**
1. ✅ Detects brand: Capterra (PPC model, 5.1M visits/month, SEO-critical)
2. ✅ Invokes `competitive-analysis` → checks G2, TrustRadius, Software Advice
3. ✅ Spawns parallel agents:
   - Design: `web-prototype-taste-brutalist` (conversion-optimized)
   - Implementation: `tdd-workflow` (revenue-critical, needs tests)
   - Validation: `performance-analysis` + `seo-audit` (page speed & SEO)
4. ✅ Validates: A/B test on 50 categories, tracks PPC CTR + time-to-click
5. ✅ Result: ↓14% time-to-click, PPC CTR +2%, organic ranking holds → SHIP

### Example 2: Trust-Critical Feature
> "Improve advisor matching for Software Advice"

**Trio automatically:**
1. ✅ Detects brand: Software Advice (PPL model, advisor-mediated, form-driven)
2. ✅ Spawns 3 parallel explorations:
   - `deep-research`: Ethnographic study of advisors + buyers
   - `web-prototype`: Instrumented prototype with variants
   - `competitive-analysis`: How competitors handle matching
3. ✅ Synthesizes: All three converge on need for pre-qualification form
4. ✅ Validates: A/B test with form fill rate + lead quality metrics
5. ✅ Result: ↑10% conversion, ↑15% advisor confidence → SHIP

### Example 3: Enterprise Feature
> "Build Grid category page improvements for G2"

**Trio automatically:**
1. ✅ Detects brand: G2 (enterprise, subscription, data-rich)
2. ✅ Loads: Enterprise reliability requirements, data accuracy focus
3. ✅ Selects skills:
   - Design: `web-prototype-taste-soft` (enterprise polish)
   - Implementation: `tdd-workflow` + `agent-architecture` (reliability)
   - Validation: Data accuracy + vendor value metrics
4. ✅ Coordinates: Architecture design → Implementation → Extensive testing
5. ✅ Result: High-polish, reliable, data-accurate Grid improvements

---

## 🎓 For Different Roles

<table>
<tr>
<td width="33%" valign="top">

### 🎨 For Designers

**Get engineering and PM perspectives:**
- Feasibility checks on complex interactions
- Business rationale for design constraints
- Metric validation for UX improvements
- Accessibility tradeoffs with clear decisions

**Auto-invoked skills:**
- `wireframe-sketch` for quick explorations
- `web-prototype-taste-*` for brand-specific prototypes
- `ui-ux-pro-max` for accessibility deep-dives

</td>
<td width="33%" valign="top">

### 💻 For Developers

**Get UX and business context:**
- User impact of technical decisions
- PM framing for scope discussions
- Design constraints explained technically
- Validation plans for architecture choices

**Auto-invoked skills:**
- `tdd-workflow` for test-driven implementation
- `api-docs` for integration documentation
- `security-audit` for security validation
- `performance-analysis` for optimization

</td>
<td width="33%" valign="top">

### 📊 For Product Managers

**Get technical + UX grounding:**
- Engineering feasibility upfront
- UX implications surfaced early
- Forced disagreement prevents groupthink
- Validation frameworks built-in

**Auto-invoked skills:**
- `deep-research` for user understanding
- `competitive-analysis` for market context
- `pm-spec` for opportunity framing
- `goal-plan` for roadmap strategy

</td>
</tr>
</table>

---

## 🔥 Advanced Features

### Parallel Agent Spawning

For complex tasks, the trio spawns multiple agents simultaneously:

```python
# Example: Build + Validate simultaneously
spawn_parallel([
    Agent(skill="web-prototype-taste-brutalist", task="Design UI"),
    Agent(skill="tdd-workflow", task="Implement backend"),
    Agent(skill="competitive-analysis", task="Research competitors")
])
→ All complete in parallel
→ Synthesize into cohesive recommendation
```

### Brand-Aware Skill Selection

Same request, different execution based on brand:

| Request | Capterra | Software Advice | G2 |
|---------|----------|-----------------|-----|
| "Prototype feature X" | `taste-brutalist` (conversion) | `taste-editorial` (trust) | `taste-soft` (polish) |
| Validate | PPC CTR + page speed | Form fills + lead quality | Data accuracy + vendor NPS |
| Implementation | Performance-critical | PII handling critical | Test-driven, reliable |

### Iterative Refinement

When validation fails, the trio automatically pivots:

```
Attempt 1: Score (0-100) → FAILED (users confused)
     ↓
Analyze failure → Designer: "Numbers are meaningless"
     ↓
Pivot: Hot/Warm/Cold tiers with guidance
     ↓
Re-validate → SUCCESS (↑12% conversion)
```

---

## ❓ FAQ

<details>
<summary><b>How does the orchestration system work?</b></summary>

The skill automatically detects your task phase (Discovery/Design/Implementation/Validation), loads brand-specific context, and selects appropriate sub-skills from a curated registry of 50+ specialized skills. Primary skills invoke automatically; secondary skills are suggested.

</details>

<details>
<summary><b>Do I need to install all 50+ sub-skills?</b></summary>

No! The orchestration system works whether or not sub-skills are installed. If a skill is not installed, the trio offers to do the work inline and suggests installing the skill for better results next time.

</details>

<details>
<summary><b>Can I customize the skill selection logic?</b></summary>

Yes! Edit the files in `trinity/skills-registry/` to adjust which skills are used for which contexts. The system is fully customizable.

</details>

<details>
<summary><b>Does it work for platforms outside the G2 group?</b></summary>

The skill is optimized for Capterra, Software Advice, GetApp, and G2 with brand-specific context. For other products, it will still provide the three-lens framework and orchestration, but without brand-specific heuristics.

</details>

<details>
<summary><b>How do I see which sub-skills were used?</b></summary>

The trio's output includes a "Sub-Skills Used" section listing which skills were invoked and what they produced.

</details>

<details>
<summary><b>Can I disable automatic skill invocation?</b></summary>

Yes. Tell the trio "no sub-skills this session" and it will only suggest skills, never invoke them automatically.

</details>

<details>
<summary><b>What if the three perspectives agree?</b></summary>

Real agreement is fine! But the skill pushes hard to find genuine tension. If all three POVs converge easily, it will explain why that convergence is real rather than staging fake disagreement.

</details>

---

## 🛠️ Contributing

Found a way to make this better? Contributions are welcome!

1. Fork the repo
2. Create a feature branch (`git checkout -b feature/amazing-improvement`)
3. Make your changes to files in `trinity/`
4. Test your changes (`claude skill install trinity/`)
5. Commit with clear messages
6. Push to your fork
7. Open a Pull Request

### Areas We'd Love Help With

- 📝 More worked examples for common product decisions
- 🌍 Translations of reference materials
- 🎨 Additional design heuristics for emerging patterns
- 💻 Developer reference updates for new tech stacks
- 📊 PM frameworks for newer discovery methods
- 🤖 New sub-skill integrations for the orchestration system

---

## 📜 License

MIT License - see [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

Built for the product teams at G2, Capterra, Software Advice, and GetApp — where great products are built through healthy disagreement, rigorous validation, and intelligent orchestration.

**Special thanks** to the Claude Code ecosystem for making skill-to-skill orchestration possible.

---

## 🚀 Get Started

Ready to make better product decisions with intelligent orchestration?

```bash
# Install the skill
claude skill install product-trio.skill

# Start your next conversation
claude
> "Should we add AI summaries to Capterra category pages?"
```

The trio will automatically orchestrate the right skills, coordinate parallel work, and give you a comprehensive, brand-aware recommendation.

---

<p align="center">
  <b>Three perspectives. Intelligent orchestration. Better decisions.</b><br>
  <a href="#installation">Install Product Trio</a> and start building.
</p>

<p align="center">
  Made with ❤️ for product people who value multiple perspectives
</p>
