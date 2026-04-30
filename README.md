# 🎯 Product Trio

> **Transform Claude into your senior product team** — Designer, Developer, and Product Manager working together on every decision.

<p align="center">
  <img src="product-trio-hero.jpg" alt="Product Trio - Three perspectives, one decision" width="100%">
</p>

<p align="center">
  <a href="https://github.com/lsanchez-g2/g2-prod-trinity/releases"><img src="https://img.shields.io/github/v/release/lsanchez-g2/g2-prod-trinity?style=flat-square" alt="Latest Release"></a>
  <a href="#installation"><img src="https://img.shields.io/badge/claude-skill-purple?style=flat-square" alt="Claude Skill"></a>
  <a href="#license"><img src="https://img.shields.io/badge/license-MIT-blue?style=flat-square" alt="License"></a>
</p>

---

## 🌟 What is Product Trio?

Product Trio is a Claude Code skill that gives you **three expert perspectives** on every product decision. Instead of one-dimensional answers, you get the full picture: what users need (Designer), what's technically feasible (Developer), and what drives business value (Product Manager).

**Built specifically for G2's ecosystem**: Capterra, Software Advice, GetApp, and G2.

### ✨ Why You'll Love It

- 🎨 **Designer POV** — User experience, accessibility, information architecture, trust signals
- 💻 **Developer POV** — Technical feasibility, scalability, implementation complexity, AI/ML tradeoffs
- 📊 **PM POV** — Business outcomes, metrics, opportunity cost, validation strategy
- ⚡ **Mandatory Disagreement** — Surfaces real tradeoffs instead of false consensus
- 🎯 **Brand-Aware** — Automatically loads context for Capterra, Software Advice, GetApp, or G2
- 🔍 **Validation Plans** — Every major decision includes testable assumptions and cheap experiments

---

## 📦 Installation

### Quick Start (Recommended)

1. **Download the latest release**
   ```bash
   # Download from releases page or use curl
   curl -L https://github.com/lsanchez-g2/g2-prod-trinity/releases/latest/download/product-trio.skill -o product-trio.skill
   ```

2. **Install the skill**
   ```bash
   claude skill install product-trio.skill
   ```

3. **Start using it** — The skill activates automatically when you work on product decisions!

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
claude skill list
```

You should see `product-trio` in your installed skills.

---

## 🚀 How to Use

The skill **activates automatically** when you work on:

- ✅ Feature specs or PRDs
- ✅ Design reviews and UX decisions
- ✅ Technical architecture calls
- ✅ Prioritization and roadmapping
- ✅ Discovery and opportunity framing
- ✅ AI feature design (models, evals, latency, cost)
- ✅ Review-related decisions
- ✅ Vendor or buyer experience work

### Example Session

**You ask:**
```
We're thinking about adding an AI-generated category summary at the top 
of Capterra category pages. Should we launch this in Q3?
```

**Product Trio responds with:**

```
POV Designer
[Analysis of scan patterns, verification needs, degraded states...]

POV Developer  
[Implementation architecture, eval harness, SEO implications...]

POV Product Manager
[Business outcomes, metrics, sequencing, validation plan...]

Disagreement
[Where the three perspectives pull in different directions and why...]

Recommendation
[The actual call with reasoning that survived the disagreement...]

Why
[What new information would change this recommendation...]

Validation
[Riskiest assumption + cheapest test + what signals to watch...]
```

---

## 🎓 For Different Roles

<table>
<tr>
<td width="33%" valign="top">

### 🎨 For Designers

Get engineering and PM perspectives on your UX decisions:

- **Feasibility checks** on complex interactions
- **Business rationale** for design constraints
- **Metric validation** for UX improvements
- **Accessibility tradeoffs** with clear decisions

</td>
<td width="33%" valign="top">

### 💻 For Developers

Context on why and business impact:

- **User impact** of technical decisions
- **PM framing** for scope discussions
- **Design constraints** explained technically
- **Validation plans** for architecture choices

</td>
<td width="33%" valign="top">

### 📊 For Product Managers

Technical + UX grounding for decisions:

- **Engineering feasibility** upfront
- **UX implications** surfaced early
- **Forced disagreement** prevents groupthink
- **Validation frameworks** built-in

</td>
</tr>
</table>

---

## 🏗️ How It Works

### Brand Detection

The skill automatically identifies which G2 platform you're working on:

| Brand | Audience | Monetization | Key Award |
|-------|----------|--------------|-----------|
| **Capterra** | SMB mass market | PPC | Shortlist |
| **Software Advice** | SMB seeking help | Pay-per-lead | FrontRunners |
| **GetApp** | Tech-forward SMB | PPC, EU-leaning | Category Leaders |
| **G2** | Mid-market + Enterprise | Subscription + intent data | Grid |

### Experience Side Detection

Automatically determines whether you're working on:

- **Vendor Experience** — Profiles, review responses, lead delivery, vendor dashboard, ads
- **Buyer Experience** — Search, category pages, product pages, comparison, reviews, AI guidance

### Progressive Context Loading

The skill loads only what's needed:

```
Your Question
    ↓
Brand + Side Detection
    ↓
Load Relevant Context
    ├─ Brand Deep-Dive (Capterra/G2/GetApp/Software Advice)
    ├─ Experience Lens (Vendor/Buyer)
    └─ Role Heuristics (Designer/Developer/PM)
    ↓
Three-Lens Analysis
    ↓
Structured Output
```

---

## 📚 What's Inside

```
g2-prod-trinity/
│
├── 📄 product-trio.skill          # Ready-to-install package
├── 📖 README.md                   # This file
│
└── trinity/                       # Source skill
    ├── 📋 SKILL.md               # Main skill logic
    │
    ├── 🏢 brands/                # Platform-specific context
    │   ├── capterra.md
    │   ├── g2.md
    │   ├── getapp.md
    │   └── software-advice.md
    │
    ├── 👁️ lenses/                # Experience perspectives
    │   ├── buyer-experience.md
    │   └── vendor-experience.md
    │
    └── 📚 references/            # Deep heuristics
        ├── pov-designer.md
        ├── pov-developer.md
        ├── pov-pm.md
        ├── disagreement-patterns.md
        └── capterra-buyer-ai-category-summary.md  # Worked example
```

---

## ❓ FAQ

<details>
<summary><b>Do I need to explicitly invoke the skill?</b></summary>

No! The skill activates automatically when you're working on product decisions. Just describe what you're working on in natural language.

</details>

<details>
<summary><b>Will it work for platforms outside the G2 group?</b></summary>

The skill is optimized for Capterra, Software Advice, GetApp, and G2 with brand-specific context. For other products, it will still provide the three-lens framework but without brand-specific heuristics.

</details>

<details>
<summary><b>Can I use this for technical decisions only?</b></summary>

Absolutely! Even if you're a developer asking a purely technical question, getting the Designer and PM perspectives often reveals important considerations you might have missed.

</details>

<details>
<summary><b>What if the three perspectives agree?</b></summary>

Real agreement is fine! But the skill pushes hard to find genuine tension. If all three POVs converge easily, it will explain why that convergence is real rather than staging fake disagreement.

</details>

<details>
<summary><b>Does it work in languages other than English?</b></summary>

Yes! The skill matches the language you use. Ask in Spanish, get answers in Spanish. The framework remains the same.

</details>

<details>
<summary><b>How do I update the skill?</b></summary>

```bash
# Download the new version
curl -L https://github.com/lsanchez-g2/g2-prod-trinity/releases/latest/download/product-trio.skill -o product-trio.skill

# Reinstall (this updates the existing skill)
claude skill install product-trio.skill
```

</details>

<details>
<summary><b>Can I customize it for my team's needs?</b></summary>

Yes! Clone the repo, edit the files in `trinity/`, and install from your local source:

```bash
git clone https://github.com/lsanchez-g2/g2-prod-trinity.git
cd g2-prod-trinity/trinity

# Edit files as needed
vim brands/capterra.md

# Install your custom version
claude skill install .
```

</details>

<details>
<summary><b>What's the "mandatory disagreement" philosophy?</b></summary>

Fake consensus is worse than no analysis. The skill forces each POV to surface real tensions — speed vs. quality, scope vs. timeline, delight vs. revenue. If you're not seeing where the roles pull in different directions, you're not pushing hard enough on at least one of them.

</details>

---

## 🎯 Real-World Example

**Question:**
> "Estamos pensando añadir un bloque de resumen generado por IA al principio de las category pages en Capterra. ¿Lo lanzamos en Q3?"

**Detects:**
- Brand: Capterra
- Side: Buyer Experience
- Loads: `capterra.md`, `buyer-experience.md`, three POV references

**POV Designer:**
- Scan patterns vs. read patterns in SMB buyer behavior
- Verification signals needed (where does this claim come from?)
- Degraded states for new/small categories

**POV Developer:**
- Batch generation (not per-pageview) for 900-2000 categories, 5.1M visits/month
- Eval harness to prevent hallucinations at scale
- SEO implications of AI-generated content on category pages

**POV Product Manager:**
- Outcome: faster time-to-shortlist
- Metrics: time-to-first-product-click, CTR to relevant profiles
- Validation: A/B test on 50 mid-sized categories first

**Disagreement:**
- Designer wants comprehensive verification citations (UX trust)
- Developer warns this adds complexity and latency (technical cost)
- PM wants MVP launch to validate hypothesis quickly (opportunity cost)

**Recommendation:**
Launch in Q3 with **phased rollout**: 50 mid-sized categories, batch generation with 24h TTL, citation links to top 3 products mentioned, eval harness with 95%+ accuracy threshold, fallback to "no summary" for edge cases.

**Validation:**
Run for 2 weeks, watch time-to-first-click and lead quality. If click time decreases >10% AND lead quality holds, expand to 200 categories in Q4.

---

## 🛠️ Advanced Usage

### Working Across Multiple Brands

```
"We're considering the same AI summary feature across Capterra and GetApp. 
How should the implementation differ?"
```

The skill will analyze each brand separately and surface the key differences (Capterra's SMB scan-first behavior vs. GetApp's comparison-driven EU audience).

### Discovery Framing

```
"Help me frame the discovery work for improving vendor profile completion rates"
```

Gets you an opportunity-solution tree, riskiest assumptions, and cheap validation experiments from the PM POV, informed by Designer (what friction exists?) and Developer (what instrumentation do we need?).

### AI Feature Design

```
"We want to add semantic search to G2 product pages. What model should we use?"
```

The skill will cover:
- **Designer**: latency perceived as "slow", error states, relevance feedback UI
- **Developer**: model options (OpenAI, Anthropic, open-source), eval strategy, cost at scale
- **PM**: incremental value over keyword search, metrics to prove it, rollout plan

---

## 🤝 Contributing

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

---

## 📜 License

MIT License - see [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

Built for the product teams at G2, Capterra, Software Advice, and GetApp — where great products are built through healthy disagreement and rigorous validation.

---

<p align="center">
  <b>Ready to make better product decisions?</b><br>
  <a href="#installation">Install Product Trio</a> and start your next conversation with Claude.
</p>

<p align="center">
  Made with ❤️ for product people who value multiple perspectives
</p>
