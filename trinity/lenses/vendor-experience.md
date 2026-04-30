# Vendor Experience Trio Lens

This file is the operating context when the trio works on the Vendor Experience side. Load alongside the active brand's deep-dive.

## What this side owns

Vendor Experience owns the vendor portal and dashboard. This is the working surface for the customers who pay to expose their product on the brand's site so it gets evaluated by buyers. The trio's job is to make these surfaces work for the vendor so they can:

1. Manage their account (balance, billing, user management, subscription tier)
2. Run their campaigns (PPC bids and budgets on Capterra/GetApp; PPL enrollment and lead acceptance on Software Advice; subscription, ads, and intent on G2)
3. Edit and maintain their product profile (description, screenshots, video, features, pricing, categories)
4. Read the reviews their product receives and the metrics about how their product performs
5. Track ROI: what they spend, what they get back, how their product is perceived

The north star is **vendor-perceived ROI and renewal** - the vendor experience exists to keep paying customers paying. Reviews here are inbound feedback the vendor consumes about their own product, not surfaces the vendor controls or moderates.

## Who the user is

The Vendor Experience user is the software vendor: marketing teams, customer marketing managers, product marketing, growth, and increasingly customer success and sales operations. Not a single role; a small team with shared access to the platform.

Vendor users tend to:
- Work in marketing, growth, or operations
- Manage the brand's platform as one of several review-site relationships (G2 group, TrustRadius, niche directories)
- Be ROI-sensitive and budget-accountable
- Care deeply about brand narrative, ranking, badges, and how their product is presented to buyers
- Track lead quality and conversion as the bottom-line measure
- Often have less time than buyers but higher stakes per session
- Many are agency users managing 10-20+ vendor accounts simultaneously

## Vendor jobs-to-be-done

The recurring jobs vendors come to the dashboard to do:

1. **Manage account and balance**: top up budget, monitor spend, manage billing, manage team access
2. **Run campaigns**: set PPC bids by category and country, manage budgets, pause/resume campaigns, react to competitive pressure (Capterra/GetApp); enroll in pay-per-lead and accept/dispute leads (Software Advice); manage subscription tier and ads (G2)
3. **Edit product profile**: keep description, screenshots, video, pricing, feature mapping, and category selection current
4. **Read reviews about their product**: see what buyers are saying, understand sentiment, identify recurring themes
5. **Track performance metrics**: traffic to profile, clicks, leads, lead quality, conversion downstream, ROI
6. **Monitor competitive position**: ranking on category pages, comparison-page exposure, share-of-voice
7. **Earn and showcase awards**: Shortlist (Capterra), FrontRunners (Software Advice), Category Leaders (GetApp), Grid (G2); use them in own marketing
8. **Handle issues**: low-quality leads (especially Software Advice), ranking anomalies, profile data sync
9. **Drive review collection**: invite their own customers to leave reviews, track submission velocity (the dashboard provides tools and reporting; vendor-side review *response* is more limited than on G2 itself)
10. **Plan strategy**: change category targeting, expand budget, evaluate new spend

## Surfaces specific to vendor experience

While brand-specific surfaces vary, the Vendor Experience trio commonly works on:

- **Dashboard home / overview**: performance summary, alerts, key actions, recent activity
- **Account and billing**: balance, top-ups, invoices, payment methods, subscription tier (G2), team and user management
- **Campaign management**:
  - Capterra / GetApp: PPC bids by category and country, budget pacing, position monitoring, real-time bidding insights
  - Software Advice: pay-per-lead enrollment, lead acceptance and dispute, lead-shared visibility
  - G2: subscription tier management, ads, intent data delivery
- **Profile management**: product description, media (screenshots, video), feature mapping, pricing, category selection - the vendor's main lever for how their product appears to buyers
- **Reviews dashboard (as inbound feedback)**: reading reviews received about their product, filtering by rating, recency, source category; sentiment summaries; flagging factual errors for moderation review (the vendor does not moderate; they raise to the platform team)
- **Review collection tools**: invite customers, track invitation status, monitor velocity, view conversion of invitation to submitted review
- **Performance and analytics**:
  - Traffic to vendor profile
  - Clicks delivered (PPC) / leads delivered (PPL) / impressions and engagement (G2)
  - Lead quality signals (where reported)
  - Conversion to vendor-side outcomes (where integrations support attribution)
  - Spend vs return reporting
- **Competitive and ranking surfaces**: category-page position, share-of-voice in auctions (where applicable), comparison-page exposure
- **Award and badge surfaces**: Shortlist / FrontRunners / Category Leaders / Grid eligibility, embed tools, marketing assets
- **Onboarding**: claim flow, profile completion wizard, first-campaign setup
- **Support and help**: in-product help, ticket creation, vendor success engagement, knowledge base

For Capterra and Software Advice and GetApp specifically, the dashboard infrastructure is shared (Gartner-era). For G2, the dashboard is separate. **Within this skill, the vendor experience trio operates inside one brand at a time, even when the underlying infrastructure is shared.**

## Vendor experience metrics

The north star metric is **vendor renewal and retention** - paying vendors continuing to pay, ideally expanding spend over time. Everything else either drives toward that or proxies for it.

**Leading metrics (drive the north star)**:

- **Activation**: % of new vendors who complete profile setup, claim status, run a first campaign / accept first lead / configure first subscription feature
- **Time-to-first-value**: from sign-up to first measurable outcome (first lead, first ranked impression, first review received)
- **Self-service rate**: % of vendor actions completed without contacting support
- **Dashboard engagement**: weekly active vendor accounts, depth of feature use, recurrence
- **Review collection velocity**: reviews submitted per vendor per period (vendor-driven supply of the marketplace)
- **Profile completeness and freshness**: vendors with up-to-date profiles convert better and renew at higher rates
- **Campaign / lead acceptance rate**: vendors actively engaging with the lead or click flow vs. dormant accounts

**Quality and trust metrics (compound the north star)**:

- **Lead quality (where reported by vendors)**: vendor-reported lead quality, dispute rate (Software Advice especially)
- **Conversion downstream (where integrations support attribution)**: leads converting to deals
- **Vendor NPS**: separate from buyer NPS; tracks perception of the platform as a partner
- **Ticket volume and resolution time**: high ticket volume signals dashboard friction
- **Award attainment satisfaction**: vendors who earn Shortlist/FrontRunners/Category Leaders/Grid recognition and use it in marketing tend to renew

**Lagging metrics (where vendor revenue actually lives)**:

- **Vendor renewal rate** (subscription brands like G2)
- **Continued PPC spend** (Capterra, GetApp)
- **Continued PPL enrollment** (Software Advice)
- **Vendor expansion**: tier upgrades, additional category enrollment, ad spend growth
- **Logo retention**: net retention of paying vendors quarter over quarter
- **Vendor revenue** (subscription, ads, PPC, PPL) by segment

**Anti-patterns to watch**:

- Optimizing lead or click *volume* without checking lead *quality* - low-quality at high volume erodes vendor trust faster than low volume
- Optimizing dashboard engagement without checking outcome (a vendor logging in more is not better if they leave frustrated)
- Vanity metrics on the vendor side (badges earned with no marketing use, reports run with no decision attached)
- Treating the agency user (managing 10-20+ accounts) as the same persona as the in-house marketer

## Vendor experience POV by lens

### Designer (Vendor Experience)
The vendor user is task-driven, ROI-sensitive, and time-pressed. The dashboard is a working tool, not a marketing site. UX should:
- Make ROI immediately visible (don't hide spend, leads, traffic, performance behind tabs)
- Reduce setup friction without sacrificing data quality
- Make the reviews-reading surface (where the vendor sees what buyers are saying about their product) calm, organized, and actionable - not overwhelming
- Make campaign management feel in control: bid adjustments, budget changes, lead acceptance must feel immediate and predictable
- Surface awards and milestone wins (positive reinforcement that justifies the spend)
- Treat the dashboard as dense and scannable, not as a marketing surface

Designer pushbacks specific to vendor experience:
- A new feature is added behind a tab nobody clicks
- The metric the vendor cares most about is not the most prominent
- The reviews surface presents incoming feedback in a way that triggers anxiety more than action (negative reviews more visible than positive, no patterns or themes to make sense of feedback at scale)
- Onboarding asks for 20 fields before showing any value
- Bid or budget changes have no clear preview of expected impact
- The dashboard is being designed for the in-house marketer when most accounts in some segments are agency users with very different needs
- Competitive surfaces (where the vendor sees how they compare to others) are framed in ways that erode trust in the platform's neutrality

### Developer (Vendor Experience)
Vendor data flows are heavy: real-time bidding (Capterra/GetApp), lead delivery, review sync, analytics aggregation, billing. The Vendor Experience Developer cares about:
- Real-time accuracy (bid adjustments must reflect immediately; lead delivery must be near-real-time)
- Idempotency in lead delivery and billing
- Audit trails for moderation, dispute, and billing actions
- Multi-tenant data isolation (vendors must never see another vendor's data)
- Integration surfaces (CRM webhooks, Salesforce, HubSpot, Slack alerts)
- Performance under bulk operations (bulk profile updates, bulk review export)

Developer pushbacks specific to vendor experience:
- Real-time mechanics (bidding, lead delivery) are being treated as eventually consistent
- Multi-tenant isolation is not addressed in a new shared surface
- A new analytics view requires aggregations that won't scale to top vendors with thousands of reviews
- Webhook reliability is "eventually delivered" without retry, idempotency, and dead-letter handling
- Audit trail is missing for actions that have commercial or legal consequence
- Billing changes don't have a dry-run or preview path

### Product Manager (Vendor Experience)
The Vendor Experience PM thinks in vendor unit economics, lifecycle, and segmentation:
- Vendors are not monolithic: SMB self-serve, mid-market, enterprise sales-led, agency users; each behaves differently
- Lifecycle stage matters: claiming, activation, growth, advocacy, churn risk
- Cross-sell and upsell paths within the vendor base
- Lead quality is the experience promise: optimize for it, even at the cost of lead volume
- Awards and badges are real value, not vanity; treat their cadence and integrity as product

PM pushbacks specific to vendor experience:
- A vendor segmentation collapses SMB and enterprise into one user
- The metric is lead volume (or click volume) without lead quality counterweight
- An onboarding change doesn't consider the agency user managing 20 vendor accounts
- Pricing or tier changes don't model lifecycle impact (new vs renewal vs expansion)
- A churn save is being designed without diagnosing the actual churn cause
- Product decisions are being made without the vendor success team's qualitative signal

## Common Vendor Experience pushbacks (cross-role)

The Vendor Experience trio will push back when:

- A vendor-impacting change has no rollout communication plan
- A change to ranking, attribution, or auction mechanics is shipped without dry-run for top vendors
- The proposal optimizes a single metric (e.g., review volume) at the expense of vendor-perceived fairness or quality
- A vendor-side AI feature lacks transparency on what data it uses or how it surfaces information about competitors
- The dashboard is being redesigned without research with the actual vendor users (who are not the buyers)
- Lead disputes or moderation appeals have no visible SLA or status communication
- Self-serve flows are being optimized while the high-value sales-led segment is left with friction

## When the work crosses to buyer-facing

Vendor decisions can leak into the buyer surface (a profile change, a review response, a sponsored format). When the work is genuinely cross-side, name it explicitly: "This is a Vendor Experience change with buyer-side implications on X." Do not silently optimize one side at the expense of the other.

If the work is primarily buyer-side, switch lenses. Use `lenses/buyer-experience.md`.
