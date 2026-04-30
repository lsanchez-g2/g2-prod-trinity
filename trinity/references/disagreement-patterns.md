# Disagreement Patterns

The most common failure mode of multi-perspective frameworks is **simulated agreement**: three voices saying the same thing in three accents. This file is the antidote.

## Why disagreement matters

A product trio adds value at the seams. If Designer, Developer, and PM converge instantly, one of three things is true:

1. The question is operational, not strategic (a single-lens answer would do)
2. Two of the three are not pulling their weight
3. The disagreement is being suppressed for the sake of harmony

In all three cases, the user is poorly served. The job is to surface the seams, name them, and resolve them with a recommendation. Not to manufacture consensus.

## Productive vs unproductive disagreement

**Productive** disagreement:
- Names a tradeoff explicitly (speed vs quality, simple vs flexible, local vs global)
- Has different evidence on each side
- Resolves with a decision rule (under condition X, do A; otherwise do B)
- Identifies what would change the call

**Unproductive** disagreement:
- Restates the same concern in three different vocabularies
- Argues about taste with no anchor
- Refuses to commit to a recommendation
- Hides behind "it depends" with no specification of what it depends on

Aim for productive. If the disagreement is unproductive, collapse it back into a single voice and explain why.

## Common tension axes

These are the seams where the three lenses pull. Pattern-match against them.

### Designer vs PM
- **User delight vs business outcome**: the design that converts best is rarely the one users prefer most
- **Cohesion vs experimentation**: designers want a coherent system, PMs want to test variants
- **Research depth vs ship cadence**: more research lowers risk and slows shipping
- **Universal access vs primary persona**: serving everyone vs serving the buyer best

### Designer vs Developer
- **Ideal interaction vs realistic complexity**: the spec assumes server response speeds the backend cannot deliver
- **Pixel fidelity vs maintainability**: a unique component for one screen vs reusing a system component
- **Animation richness vs performance**: motion that delights at 60fps and crawls on mid-tier hardware
- **Customization vs constraint**: how many edges can the user configure before the system breaks

### Developer vs PM
- **Feature velocity vs technical debt**: shipping faster now slows shipping later
- **Build vs buy**: vendor lock-in vs build cost
- **Scope vs simplicity**: the additional capability that doubles the surface area
- **Real-time vs eventually consistent**: the perceived UX gain vs the operational cost

### Three-way tensions (the most interesting)
- **AI-powered features**: Designer wants explainability; Developer wants determinism; PM wants the metric to move. All three pull the spec in different directions.
- **Scope of an MVP**: Designer wants the experience to be good; Developer wants the architecture to be defensible; PM wants the smallest test that resolves the riskiest assumption.
- **Personalization**: Designer worries about cohesion and surprise; Developer worries about cold start and infrastructure; PM worries about whether the lift justifies the cost.

## Forcing functions when stuck

When the three POVs are agreeing too easily, run one of these:

### The "double the constraint" check
Ask: what if we had to ship this in half the time? At twice the budget? With one fewer engineer? With double the user load? Which lens breaks first?

### The pre-mortem
Six months from now, this feature failed. Each lens names the most likely cause:
- Designer: "users couldn't find it / didn't understand it / didn't trust it"
- Developer: "it didn't scale / was always broken / blocked other work"
- PM: "we measured the wrong thing / solved the wrong problem / didn't validate"

If two lenses name the same cause, the disagreement was hiding.

### The "explain to your counterpart" test
Designer explains the spec back to the PM. Developer explains the metric back to the PM. PM explains the architecture back to the Developer. Where the explanation breaks is where the disagreement is.

### The "minimum viable disagreement"
Force at least one specific tradeoff to be named, with a decision rule. Example: "If activation rate after 30 days is below 25%, we kill the AI summarization entry point and keep the manual one." Without a number and a rule, the disagreement is decorative.

## How to resolve disagreement in the recommendation

When you have surfaced real tension, the recommendation chooses one of:

1. **Sequence**: do the safer thing first, the riskier thing later (with the gate that opens it)
2. **Split**: do both partially, with each role's concern addressed in the smaller version
3. **Defer**: name the experiment whose result would resolve the disagreement
4. **Decide**: pick a side, explicitly, and own the tradeoff

Avoid:
- "Do all of them" (you cannot, and pretending you can is the failure mode)
- "Let the team decide" (the trio is the team; this is buck-passing)
- "It depends" without saying on what

## When disagreement is staged

If you find yourself manufacturing tension to fill the section, stop. Write:

> "The three lenses converge here because [specific reason]. The risk to watch is [the lens-specific concern that would re-open the disagreement if it changes]."

Convergence is fine when it is real. It is a problem when it is performed.

## When the framework gets in the way

Some questions do not benefit from three POVs:

- **Pure execution questions**: "what's the syntax for X" - the framework is overhead
- **Aesthetic-only questions**: "which of these two color palettes" - one lens carries it
- **Crisis response**: "the site is down" - the trio framing slows the answer

In these cases, drop the structure, answer directly, and surface the trio framing only if a deeper question lurks behind the surface one.
