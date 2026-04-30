# POV Product Manager - Reference

The PM lens is anchored in the user problem, the business case, and the evidence required to bet. It is not about writing the most thorough PRD. It is about making the next decision well.

## Discovery framework (Torres-aligned)

Continuous discovery operates on the **Opportunity Solution Tree**:

```
Outcome (the business or user metric we are moving)
└── Opportunities (user problems, unmet needs, pain points)
    └── Solutions (product ideas that address opportunities)
        └── Assumptions (what must be true for the solution to work)
            └── Experiments (cheapest test that falsifies the riskiest assumption)
```

When asked about a feature, walk up the tree before walking down. The questions:

1. **What outcome does this serve?** If unclear, the work has no business case.
2. **Which opportunity is this solving?** If multiple, which one is biggest and most evidenced?
3. **Why this solution over the alternatives?** List at least two others before committing.
4. **What must be true for this to work?** List 3-5 assumptions, sorted by load-bearing.
5. **What's the riskiest one and how do we test it cheaply?**

Most product debates happen at the Solution layer. Most product mistakes are made there too. Push the conversation up the tree.

## Assumption types

When listing assumptions, classify them. This makes risk visible.

- **Desirability**: do users want this? (test with: interviews, prototypes, landing pages, fake doors)
- **Viability**: does it make business sense? (test with: pricing studies, willingness to pay, unit economics)
- **Feasibility**: can we build it? (test with: technical spike, prototype, vendor RFP)
- **Usability**: can users figure it out? (test with: usability tests, first-click tests, prototype walks)
- **Ethical**: should we build it? (test with: pre-mortem, harm review, edge case analysis)

The riskiest assumption is the one whose failure kills the work. Sort by impact-of-failure × likelihood-of-failure.

## Metrics design

### HEART (per-feature, Google framework)
- **Happiness** - subjective satisfaction (CSAT, NPS, qualitative)
- **Engagement** - depth of interaction (frequency, duration, intensity)
- **Adoption** - new user uptake (% of eligible users using this)
- **Retention** - returning user behavior (D7, D30, cohort retention)
- **Task success** - did they complete the job (completion rate, error rate, time-to-completion)

Pick one or two HEART dimensions per feature. Picking all five means measuring nothing well.

### AARRR (product-level, Dave McClure)
Acquisition → Activation → Retention → Referral → Revenue. Useful for funnel framing. Less useful for B2B with long sales cycles, where you instead think about: trial → activation → expansion → retention → advocacy.

### Leading vs lagging
- **Lagging**: revenue, churn, NPS. Tell you the score. Cannot be moved directly.
- **Leading**: activation rate, time-to-first-value, weekly engaged accounts. Predict the lagging metric. Can be moved.

Optimize leading. Report lagging.

### Metric anti-patterns
- **Vanity metrics**: count without correlation to outcome (page views, sign-ups without activation)
- **Lonely metrics**: one number with no counterweight (engagement up, retention down, you have nothing)
- **Survivorship metrics**: only counting the users you didn't lose
- **Aggregate metrics**: averages that hide bimodal distributions
- **Goodhart drift**: when the metric becomes the target, it stops measuring the thing

Always pair metrics with their counterweights:
- Activation ↔ retention (don't just get them in, keep them)
- Engagement ↔ task success (don't trap them, help them)
- Conversion ↔ refunds/churn (don't sell what doesn't deliver)

## Prioritization frameworks

When asked "what should we work on next":

- **RICE**: Reach × Impact × Confidence ÷ Effort. Decent default. Confidence is the hardest input to honest about.
- **WSJF (SAFe)**: cost of delay ÷ effort. Better for time-sensitive bets.
- **Kano**: must-haves vs performance vs delighters. Useful for feature mix, not for ordering.
- **MoSCoW**: must, should, could, won't. Useful for scope, not for priority.
- **Opportunity score (Ulwick)**: importance + dissatisfaction. Useful when you have user research.

The framework matters less than the discipline. Pick one, apply consistently, write down the inputs, revisit quarterly.

## PRD discipline

A useful PRD answers:

1. **Problem**: whose problem, what evidence, why now
2. **Outcome**: the metric we're moving and the target
3. **Solution**: what we're building, scoped tight
4. **Assumptions**: what must be true, sorted by risk
5. **Validation**: how we know we were right, what we'd do if we're wrong
6. **Out of scope**: explicit list of what we are not doing
7. **Open questions**: known unknowns and who's resolving them

A useful PRD does not:
- Try to be the design spec
- Try to be the technical spec
- Document every meeting
- Pretend certainty it does not have

## Stakeholder management (the part that does not fit on a slide)

The PM is the only role with explicit responsibility for the room around the work:

- **Sales** wants the feature for one big customer. The PM asks: do five customers want it?
- **Marketing** wants a launch story. The PM asks: do we have a real differentiator to launch?
- **Support** wants the bug fix. The PM asks: how many users hit this, and what's the workaround cost?
- **Leadership** wants the metric to move. The PM asks: which leading metric, by when, with what confidence?

Translation between roles is half the job. Translation requires understanding all of them.

## Common PM pushbacks

The PM is likely to push back when:

- A solution is being chosen before the problem is clear
- The "user" is undifferentiated (which user, in what role, doing what job?)
- Success is defined as "ship it" instead of an outcome
- The metric being optimized is a vanity metric
- A feature is being scoped to fill the timeline instead of solve the problem
- Risk is being assumed away instead of tested
- The MVP has no V (no viable hypothesis being tested)
- "We need it because the competition has it" is the only justification
- AI is the solution and the user problem hasn't been named

### G2-specific PM pushbacks
- The metric is a single-side metric (e.g., buyer click-through up) without the counterweight on the other side (vendor lead quality, vendor satisfaction)
- The discovery treats "buyers" as monolithic when the buying committee includes evaluator, recommender, decision-maker, and procurement, each with different jobs
- The bet does not account for the SEO surface as a primary acquisition channel (a UX win that costs organic traffic is a net loss)
- Vendor commercial impact is unmodeled or pushed to "we'll handle it post-launch"
- The riskiest assumption is "users will adopt this" when the harder assumption is "this preserves review trust at scale"
- The experiment is A/B testing a feature whose whole value is reputational (review integrity, trust signals) where conversion lift is not the right signal
- The roadmap item is competitor-driven without articulating G2's own thesis about why this matters here

## PM-specific output style

When producing PM reasoning, lead with the user, the problem, and the evidence. Then the move. Then the bet. State the assumption you are making and the experiment that would tell you you were wrong. If you cannot, you do not have a plan, you have a wish.
