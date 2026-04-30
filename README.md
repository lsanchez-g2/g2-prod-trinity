# Product Trio Skill

A Claude Code skill that applies a Product Trio reasoning framework (Designer + Developer + Product Manager) for the G2 group's review platforms.

## Overview

This skill transforms Claude into a senior digital product trio, providing three expert lenses on the same problem. It's designed specifically for product work across the G2 group's four review platforms:

- **Capterra** - SMB mass market, PPC, Shortlist awards
- **Software Advice** - SMB seeking advisor help, pay-per-lead, FrontRunners awards  
- **GetApp** - SMB tech-forward, comparison-driven, EU-leaning, PPC, Category Leaders awards
- **G2** - mid-market and enterprise, peer-driven, subscription + intent data, Grid

## When to Use

The skill automatically activates when working on:

- Feature specification, scoping, or PRD-style writing
- Design critique, UX/UI decisions, accessibility tradeoffs
- Technical feasibility, architecture, implementation calls
- Prioritization, roadmap, sequencing
- Discovery: opportunity framing, assumption testing, validation plans
- Metrics, success criteria, instrumentation
- Cross-functional disagreements where roles see different things
- AI-powered features (model choice, UX of probabilistic output, eval, latency, cost)
- Review-related decisions (collection, display, moderation, AI summarization)
- Vendor or buyer surface changes

## Output Structure

Every response follows a structured four-lens format:

1. **POV Designer** - User-centered perspective on UX, accessibility, information architecture
2. **POV Developer** - Technical feasibility, scalability, implementation complexity
3. **POV Product Manager** - Business case, metrics, riskiest assumptions
4. **Disagreement** - Where the three lenses pull in different directions (mandatory - surfaces real tradeoffs)
5. **Recommendation** - The call, with reasoning that survived disagreement
6. **Why** - What would change the recommendation
7. **Validation** - Riskiest assumption + cheapest test + signal + decision rule

## Installation

### From GitHub Release

1. Download the latest `product-trio.skill` file from the [releases page](../../releases)
2. Install using Claude Code:
   ```bash
   claude skill install product-trio.skill
   ```

### From Source

Clone this repository and package the skill:

```bash
git clone <your-repo-url>
cd <repo-name>
cd trinity
# Package manually if needed
zip -r ../product-trio.skill . -x "*.DS_Store" "*__pycache__*" "*.pyc"
```

Then install:
```bash
claude skill install product-trio.skill
```

## Skill Structure

```
trinity/
├── SKILL.md                    # Main skill definition
├── brands/                     # Brand-specific context
│   ├── capterra.md
│   ├── g2.md
│   ├── getapp.md
│   └── software-advice.md
├── lenses/                     # Trio-side perspectives
│   ├── buyer-experience.md
│   └── vendor-experience.md
└── references/                 # Deep heuristics
    ├── pov-designer.md
    ├── pov-developer.md
    ├── pov-pm.md
    ├── disagreement-patterns.md
    └── capterra-buyer-ai-category-summary.md  # Worked example
```

## Key Features

- **Brand-Aware**: Loads the correct brand context (Capterra, Software Advice, GetApp, or G2) based on your query
- **Trio-Side Detection**: Automatically identifies whether you're working on Vendor Experience or Buyer Experience
- **Mandatory Disagreement**: Forces productive tension between perspectives to surface real tradeoffs
- **Validation Plans**: Includes falsifiable assumptions and cheap tests for major decisions
- **Worked Example**: Includes a complete worked example showing the framework in action

## Example Usage

**User**: "Estamos pensando añadir un bloque de resumen generado por IA al principio de las category pages en Capterra. ¿Lo lanzamos en Q3?"

**Skill Output**: 
- Detects brand (Capterra) and side (Buyer Experience)
- Loads relevant brand and lens context
- Provides POV Designer (scan patterns, verification, degraded states)
- Provides POV Developer (batch generation, eval harness, SEO impact)
- Provides POV Product Manager (outcomes, metrics, sequencing)
- Surfaces disagreements (e.g., Designer vs Developer on implementation approach)
- Makes a concrete recommendation with validation plan

## License

[Your License Here]

## Contributing

[Your contribution guidelines]
