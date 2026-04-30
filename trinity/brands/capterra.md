# Capterra

This file is the operating context for product decisions in Capterra. Load when the task is anchored in Capterra. Do not cross-reference other G2 group brands unless the user explicitly asks.

## What Capterra is

Capterra is a software discovery and review platform serving primarily SMB software buyers. Founded 1999, acquired by Gartner 2015, now part of G2 Digital Markets after the G2 acquisition closed February 2026.

- **Audience**: SMB mass market, broad; many first-time researchers; high mix of non-technical buyers
- **Region skew**: US-leaning, with strong global reach
- **Lead model**: PPC (pay per click) on category pages and product listings
- **Award system**: Capterra Shortlist (annual, by category)
- **Scale**: ~5.1M visits/month; ~900-2000 categories; the largest of the three G2 Digital Markets brands by traffic

## What buyers come for

The typical Capterra buyer journey:

1. Lands on a category page from organic Google search ("best [category] software")
2. Skims the top listings, mostly ranked by paid placement first, then by review-driven signals
3. Reads short reviews, looks at ratings and recent activity
4. Compares 3-5 products side by side
5. Clicks through to vendor sites or fills a contact form

Capterra buyers tend to be:
- Less technically deep than GetApp or G2 buyers
- Looking for solutions to scoped problems, often time-pressed
- Sensitive to clear ratings, badges, and trust signals (review volume + recency)
- More likely to be the buyer-decider directly (smaller orgs, less buying committee)

## What vendors come for

Vendors invest in Capterra to capture buyer demand at the moment of category research. The mechanics:

- **Paid placement**: PPC bids determine ranking on category pages above the organic listings; bids range widely by category competitiveness ($5 in low-comp categories, $20+ in saturated ones)
- **Profile optimization**: product description, screenshots, video, feature mapping, category selection - the right categories matter more than aspirational ones
- **Review collection**: review volume and recency drive both organic ranking and Shortlist eligibility
- **Shortlist awards**: annual, category-specific, used heavily in vendor marketing
- **Lead delivery**: PPC traffic to vendor site, contact form submissions, demo requests

## Surfaces and primary screens

### Buyer-facing
- Homepage and search
- Category pages (the load-bearing surface for traffic and monetization)
- Product profile pages (reviews, features, pricing, screenshots, video)
- Comparison pages (side-by-side feature and rating comparison)
- Reviews collection and reading
- Buyer guides and editorial content (SEO-driving)
- AI-driven recommendation surfaces (post-G2 acquisition direction)

### Vendor-facing
- Vendor dashboard (currently shared infrastructure with Software Advice and GetApp from the Gartner era)
- Profile management (product info, media, categories)
- Review response and moderation requests
- PPC campaign management (bids, budgets, category targeting)
- Lead and traffic analytics
- Shortlist and badge management

## Non-negotiable constraints

- **Review integrity**: zero vendor influence on review content; transparent disclosure on incentivized reviews; defensible moderation. Capterra's reputation is the asset.
- **SEO surface health**: organic search drives the majority of buyer-side traffic; any change must consider crawlability, schema markup, page speed, content uniqueness, and E-E-A-T signals
- **AEO (Answer Engine Optimization)**: a rising concern as buyers increasingly use AI tools to research; structured data and authority signals matter for AI surface visibility
- **Vendor commercial fairness**: the PPC auction must remain credible and transparent; ranking algorithm changes require vendor communication
- **Category integrity**: putting products in wrong or aspirational categories damages buyer trust; review-to-category attribution matters
- **Sponsored vs organic clarity**: paid placement must be clearly labeled; mixing creates regulatory and trust risk

## Recurring themes in the work

### AI features
- AI-generated review summaries on product and category pages
- AI-driven recommendations and shortlists
- AI assistance in buyer research (chat-style or structured guidance)
- Vendor-side AI tools (review insights, competitive analysis, content suggestions)

The recurring tension on AI: buyer value vs vendor fairness vs review integrity. Every AI surface must answer how it sources, how it handles low-data situations, how it cites, and how it avoids systematic bias against subsets of vendors.

### Review collection and quality
- Incentivized reviews (gift cards via Reviews-as-a-Service) - disclosure and integrity
- Verification methods (LinkedIn, work email, screenshots of usage)
- Review response by vendors
- Moderation queues, flagging, and appeals
- Review recency and decay in ranking signal

### Category and taxonomy
- Category creation, deprecation, and merging
- Sub-category structure and depth
- Category-level vs product-level award eligibility
- Category page UX and density

### Paid placement and ad mechanics
- PPC auction transparency
- Bid floors and ceilings
- Position vs cost tradeoffs
- Budget pacing and exhaustion behavior
- Sponsored format consistency

## Common pushbacks specific to Capterra

A Capterra-savvy trio will push back when:

- A buyer surface change ignores the SEO surface or category page primacy
- An AI feature is proposed without addressing how it handles products with fewer than ~30 reviews
- A vendor-facing change has no rollout communication and no impact analysis on PPC mechanics
- The metric being optimized is single-side (e.g., buyer click-through) without the counterweight (vendor lead quality, vendor satisfaction, review submission rate)
- The proposal treats Capterra buyers like enterprise buyers (they are not; they are SMB and time-pressed)
- A new surface breaks the "scan, compare, click" rhythm Capterra buyers have learned
- Sponsored vs organic clarity is being relaxed for any reason
- A change to ranking or attribution does not have a vendor communication plan
- The proposal references G2 group consolidation as if it were live; in product surfaces, Capterra remains independent unless the work is explicitly cross-brand

## Default assumptions when context is thin

If the user does not specify, assume:

- **Surface**: buyer-facing unless the task mentions vendors, dashboard, ads, or sellers
- **User**: anonymous buyer arriving from organic search to a category page
- **Region**: global with US bias
- **Device**: desktop primary, mobile considered
- **Brand independence**: this is a Capterra decision, not a cross-brand one

State the assumption explicitly when you make it.
