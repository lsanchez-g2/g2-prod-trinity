# Software Advice

This file is the operating context for product decisions in Software Advice. Load when the task is anchored in Software Advice. Do not cross-reference other G2 group brands unless the user explicitly asks.

## What Software Advice is

Software Advice is a software discovery platform built around a distinct model: **advisor-mediated software recommendation**. Founded 2005, acquired by Gartner 2014, now part of G2 Digital Markets after the G2 acquisition closed February 2026.

- **Audience**: SMB buyers seeking guided help, more comfortable picking up the phone or filling a form than self-serving through review pages
- **Region skew**: US-centric
- **Lead model**: pay-per-lead (PPL); fundamentally different from the PPC model used by Capterra and GetApp
- **Award system**: FrontRunners (annual, by category)
- **Scale**: ~2.5M visits/month

## What buyers come for

The Software Advice buyer journey is shaped by the advisor model:

1. Lands from search ("best [category] software"), often with a comparative or buyer-guide intent
2. Engages with content: buyer guides, advisor-curated category overviews
3. Submits a form or talks with an advisor (often by phone) describing needs, budget, team size, use case
4. Advisor presents 3-5 vendor recommendations, with balanced pros and cons
5. Buyer evaluates and converts (or not) with vendors, who paid for the lead

Software Advice buyers tend to be:
- Less self-serve than Capterra buyers, willing to invest time in conversation for tailored guidance
- Often in operations or admin roles, not technical
- More committed to a purchase (the form fill is a higher-intent signal than a click)
- Seeking validation and reassurance, not just comparison

## What vendors come for

Vendors do not bid on Software Advice the way they do on Capterra. The model is:

- **Pay-per-lead**: vendors pay a per-lead fee (typically $70-$250/lead, varying by category and qualification depth) when an advisor refers a buyer to them
- **Lead sharing**: each lead is typically shared with multiple competing vendors (~3-5), so vendor sales teams must compete to convert
- **Inclusion**: to be presented to buyers by advisors, vendors must be in the program (paid)
- **FrontRunners awards**: annual, category-specific, based on user reviews + usability/customer satisfaction methodology
- **Editorial visibility**: buyer guides, expert articles, category pages also drive visibility

## Surfaces and primary screens

### Buyer-facing
- Homepage and search
- Category pages with editorial framing (more buyer-guide style than pure list)
- Buyer guides and educational content (load-bearing for SEO)
- Advisor request forms and call-back surfaces
- Product reviews (synced with Capterra and GetApp from Gartner-era infrastructure, but presented in Software Advice's own voice)
- Editorial expert content

### Vendor-facing
- Vendor dashboard (shared infrastructure with Capterra and GetApp from Gartner era)
- Lead delivery and management
- Lead disputing (vendors can request refunds for unqualified leads, with Gartner/G2 team final decision)
- Profile management
- FrontRunners and badge management
- Reporting and analytics on lead conversion

## Non-negotiable constraints

- **Advisor independence and trust**: the advisor must be perceived as offering balanced, unbiased recommendations, not running a paid sales pitch; this is the asset Software Advice rents
- **Review integrity**: same as the rest of the group
- **Lead quality**: low-quality leads erode vendor confidence in the model and trigger churn; lead qualification is product, not just operations
- **SEO and editorial authority**: buyer guides drive a large share of organic traffic; content quality and originality matter for E-E-A-T
- **Vendor parity in advisor presentation**: vendors paying for the program expect their inclusion to be fair; systematic bias in how advisors present recommendations is a credibility risk
- **PII and form data handling**: the form fill captures more PII than a typical click; data handling must meet expectations

## Recurring themes in the work

### Lead model dynamics
- Advisor workflow tools (CRM-like surfaces for the advisor team)
- Lead qualification and matching algorithms
- Lead dispute mechanisms and adjudication
- Pricing tier design (per-lead, by category, by lead quality tier)
- AI-assisted advisor tooling (suggestions, summaries, prep before calls)

### Buyer guidance and content
- Buyer guides as the front door (not just review pages)
- Editorial workflow and expert curation
- Content depth vs. breadth tradeoffs
- AI-assisted content generation (with editorial oversight)

### Award systems
- FrontRunners methodology and category eligibility
- Award-based vendor marketing programs
- Award update cadence and surface

### AI features
- AI-assisted advisor matching
- AI-generated buyer guidance (chat-style, scoped to category and budget)
- AI summarization of reviews and product features
- Vendor-side AI tools

## Common pushbacks specific to Software Advice

A Software Advice-savvy trio will push back when:

- A change to advisor-presented recommendations is proposed without addressing how it preserves perceived neutrality
- An AI buyer-guidance feature is proposed without naming the relationship to the human advisor (replacement, supplement, gate)
- A lead-quality change is proposed without modeling the vendor-side reaction (dispute volume, churn risk, sales adoption)
- The metric being optimized is lead volume without lead quality counterweight
- A buyer-side change ignores that Software Advice buyers are often not self-serve and need editorial framing
- Editorial content is being treated as marginal when it is in fact the SEO and authority spine
- A pay-per-lead change is proposed without modeling the impact on vendor unit economics
- The proposal references G2 group consolidation as if it were live; Software Advice remains an independent product

## Default assumptions when context is thin

If the user does not specify, assume:

- **Surface**: buyer-facing unless the task mentions vendor or advisor work
- **User**: anonymous buyer with a clear category in mind, willing to engage with editorial or form content
- **Region**: US-centric
- **Lead model**: pay-per-lead is the air the platform breathes
- **Brand independence**: this is a Software Advice decision, not a cross-brand one

State the assumption explicitly when you make it.
