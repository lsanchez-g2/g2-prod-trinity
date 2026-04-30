# Buyer Experience Trio Lens

This file is the operating context when the trio works on the Buyer Experience side. Load alongside the active brand's deep-dive.

## What this side owns

Buyer Experience owns everything visible to the visitors who land on the site: web pages, directories, product profiles, reviews-as-content, SEM landing pages, category lists, comparison pages, buyer guides. The trio's job is to make these surfaces work harder for the visitor so they:

1. Find what they need fast (low friction, clear navigation)
2. Engage with the right products (interaction, comparison, review reading)
3. Come back when they are ready (return visits, recurrence)
4. Click through to vendors (the conversion event that generates revenue)

The north star is **revenue-generating click-through to vendors**, supported by recurrence and engagement quality. Reviews here are content the buyer consumes, not surfaces the buyer manages.

## Who the user is

The Buyer Experience user is the software buyer. The profile varies significantly across G2 group brands - Capterra leans SMB mass market, GetApp leans tech-forward SMB and EU, Software Advice leans SMB seeking guidance, G2 leans mid-market and enterprise. Within any one brand, treat buyers as the active user and consult the brand deep-dive for specific audience traits.

Common across brands, buyers tend to:
- Arrive from organic search (with rising share from AI-driven search)
- Be time-pressed and skeptical of marketing language
- Make decisions that affect their team or company, not just themselves
- Value peer evidence over vendor claims
- Cross-check information across multiple sources before committing
- Often return after a first visit before converting (research is rarely one-session)

## Buyer jobs-to-be-done

The recurring jobs buyers come to do, which the Buyer Experience trio designs for:

1. **Discover the category**: understand what type of software solves their problem; learn the landscape
2. **Build a shortlist**: narrow from hundreds to 5-10 candidates worth deeper review
3. **Compare options**: evaluate shortlisted products on features, price, fit, peer experience
4. **Validate with peers**: read reviews from people in similar roles or companies
5. **Decide and convert**: pick a vendor to engage; click through, fill a form, request a demo
6. **Share with the committee**: send links, comparisons, reports to colleagues for review (especially mid-market and enterprise)
7. **Return to research more deeply**: re-read reviews after vendor calls, validate claims, double-check
8. **Submit their own review**: post-purchase, contribute back to the community

## Surfaces specific to buyer experience

While brand-specific surfaces vary, the Buyer Experience trio commonly works on:

- **Homepage and entry points**: search bar, top categories, editorial features
- **Search and discovery**: keyword search, semantic search, filters, faceted navigation
- **Category pages**: the high-traffic, monetized surface across all brands
- **Product profile pages**: reviews, features, pricing, screenshots, video, vendor info
- **Comparison pages**: side-by-side, multi-product, feature-level
- **Reviews reading**: long and short reviews, filtering, sorting, depth of presentation
- **Reviews collection**: forms for buyers who want to leave a review
- **Buyer guides and editorial**: SEO-driving content that supports the buyer journey
- **Recommendation surfaces**: AI-driven suggestions, related products, alternatives
- **AI buyer guidance**: chat-style interfaces (G2.ai), structured AI assistance
- **Saved lists, shortlists, and shareable artifacts**: especially relevant for committee buyers
- **Reports and downloads**: Crowd reports, Best of, Implementation, etc. (G2-specific)
- **Vendor contact and conversion surfaces**: forms, demo requests, click-to-vendor

## Buyer experience metrics

The north star metric is **revenue-generating click-through to vendors** (the click that monetizes through PPC, fills a lead form for PPL, or triggers a measurable conversion event). Everything else is leading or supporting.

**Leading metrics (drive the north star)**:

- **Click-through to vendor**: the conversion event itself; segmented by category, surface, and buyer type
- **Form fill / demo request rate**: where the lead model is form-based (Software Advice especially)
- **Comparison surface engagement**: depth of use of the comparison tool; correlates with high-intent click
- **Review reading depth**: pages and time on review-rich pages, not just count
- **Time-to-first-meaningful-action**: from arrival to first click on a product, comparison, or review
- **Search success and refinement**: does search return what buyers expected; is refinement converging or diverging
- **Filter usage**: which filters help buyers narrow effectively toward a click
- **AI surface engagement and helpfulness**: AI surfaces are valuable only if they help the buyer click the right product faster, not just engage longer

**Recurrence and return metrics (compound the north star)**:

- **Return visit rate**: % of buyers who come back within X days
- **Multi-session conversion**: share of clicks that come from second-or-later sessions (research is multi-session for most categories)
- **Cross-page navigation depth per session**: are buyers exploring or bouncing
- **Saved lists, shortlists, comparisons**: if logged-in or session-persistent, signal of intent to return
- **Post-conversion review submission rate**: closes the marketplace loop; today's buyer becomes tomorrow's review supply

**Lagging metrics (where revenue actually lives)**:

- **Revenue from buyer-side surfaces** (PPC clicks, PPL leads, ad impressions on category pages)
- **Organic traffic share by brand and category**: the supply side of the funnel
- **Buyer-reported satisfaction** (post-decision surveys when feasible)
- **Buyer-side NPS** (separate from vendor NPS)
- **Marketplace liquidity** (review supply × buyer demand)
- **AEO visibility** (citations in AI-driven search results)

**Anti-patterns to watch**:

- Optimizing engagement metrics (time on page, pageviews) without checking the click-through downstream
- Optimizing click volume without checking lead quality (the click that doesn't convert hurts vendor trust and renewals)
- Treating return visits as a goal in itself - return visits are valuable only when they lead to a click; high return rate with no click is research that benefits no one

## Buyer experience POV by lens

### Designer (Buyer Experience)
The buyer is comparing, scanning, deciding under time pressure. The buyer surface is also the SEO surface, so design decisions affect both UX and acquisition. UX should:
- Respect the scan-first behavior (skim, then read deeper)
- Make trust signals legible (review volume, recency, reviewer profile)
- Treat empty and low-data states as designed, not afterthoughts (low-review products are common)
- Support comparison as a primary mode, not a hidden one
- Respect committee dynamics (shareable, exportable, multi-user where relevant)
- Make AI surfaces explainable (sources, citations, scope limits)

Designer pushbacks specific to buyer experience:
- A category page change ignores SEO surface implications
- AI summaries are presented without verifiable source links
- Review presentation favors flashy quotes over balanced signal
- Comparison surface gets cluttered or slow under feature-rich vendors
- Empty states on low-review products look broken instead of intentional
- Mobile is treated as second-class when buyer cross-checking on mobile is common
- Personalization is added before the base experience is solid

### Developer (Buyer Experience)
Buyer-facing surfaces are high-traffic, SEO-load-bearing, and increasingly AI-augmented. The Developer cares about:
- Page performance (Core Web Vitals, especially LCP and INP) - directly affects SEO and conversion
- Crawlability, schema markup, structured data, canonical URLs
- AI infrastructure: review corpus access, eval harness, latency budgets, cost telemetry, fallback behavior
- Caching strategies (per-page, per-corpus, with appropriate TTLs and invalidation)
- Search infrastructure (semantic search, filters, sorting at scale)
- Multi-language and i18n on EU-relevant brands

Developer pushbacks specific to buyer experience:
- A surface change degrades Core Web Vitals
- Schema markup is missing or wrong on a buyer-facing page
- AI surfaces are per-pageview when corpus-level caching is the obvious pattern
- A new filter or sort doesn't have a query plan that holds at scale
- Personalization breaks canonical URLs or creates SEO content duplication
- Internationalization is an afterthought (English-only model on Spanish reviews silently fails)
- AI streaming UX has no graceful degradation when the model is slow or down

### Product Manager (Buyer Experience)
The Buyer Experience PM thinks in buyer journey, evidence quality, and marketplace dynamics:
- The buyer journey is non-linear: discovery, shortlisting, comparison, validation, return visits
- Different buyer types (SMB self-serve, mid-market researcher, enterprise committee) need different surfaces
- The trade-off between buyer experience and vendor commercial fairness is permanent and must be managed
- AI features must be measured for decision quality, not just engagement
- Marketplace liquidity (review supply × buyer demand) is the long-term defensibility

PM pushbacks specific to buyer experience:
- A change is being measured by engagement when the underlying need is decision quality
- The buyer is treated as monolithic when the brand has clear sub-segments
- An AI feature optimizes time-to-recommendation without checking whether the recommendation is actually right
- The metric is single-side (buyer satisfaction) without the marketplace counterweight (vendor lead quality, vendor renewal)
- "Personalization" is being added without naming the cold-start strategy or the privacy posture
- Editorial and content surfaces are being treated as marketing instead of as part of the buyer journey
- A change ignores the buying committee dynamic (shareability, multi-user surfaces)

## Common Buyer Experience pushbacks (cross-role)

The Buyer Experience trio will push back when:

- A change to a buyer-facing surface has no SEO surface impact analysis
- An AI feature is shipped without an eval harness scaled to the brand's review corpus and category depth
- The decision treats buyer-side metrics in isolation from vendor-side health (the marketplace is two-sided)
- Sponsored vs organic distinction is being eroded
- Review integrity protections (verification, moderation, anti-fraud) are being relaxed for any reason
- A new buyer-side feature lacks a kill criterion or rollback path

## When the work crosses to vendor-facing

Buyer decisions can leak into the vendor surface (ranking changes, badge eligibility, attribution). When the work is genuinely cross-side, name it explicitly: "This is a Buyer Experience change with vendor-side implications on X." Do not silently optimize one side at the expense of the other.

If the work is primarily vendor-side, switch lenses. Use `lenses/vendor-experience.md`.
