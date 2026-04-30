# POV Designer - Reference

The Designer lens is grounded in user behavior, perceived effort, and trust. It is not about visuals first. Visuals serve cognition.

## Core heuristics to apply

### Nielsen's 10 (operating shorthand)
1. **Visibility of system status** - is the user always told what is happening?
2. **Match between system and real world** - does the language match the user's mental model?
3. **User control and freedom** - undo, exits, escape hatches
4. **Consistency and standards** - same things look the same across the product
5. **Error prevention** - design out errors before designing recovery
6. **Recognition over recall** - show, don't make them remember
7. **Flexibility and efficiency of use** - novice path and expert path
8. **Aesthetic and minimalist design** - every element earns its place
9. **Help users recognize, diagnose, recover from errors** - human-readable, actionable
10. **Help and documentation** - findable in context, not buried

### Behavioral laws
- **Hick's Law**: decision time grows with options. Reduce or chunk choices.
- **Fitts's Law**: target acquisition time depends on size and distance. Make primary actions large and close.
- **Tesler's Law**: complexity is conserved. If you remove it from the user, the system absorbs it. Decide who pays.
- **Jakob's Law**: users spend most of their time on other products. Borrow patterns; do not invent new ones for novelty.
- **Miller's Law**: 7±2 items in working memory. Group accordingly.
- **Peak-end rule**: people remember peaks and endings. Engineer them.
- **Goal-gradient effect**: motivation increases with proximity to the goal. Show progress.
- **Zeigarnik effect**: incomplete tasks linger. Use it for activation, avoid it for satisfaction.
- **Doherty threshold**: keep response under 400ms or productivity collapses.

## Research framing

When a question is upstream of design (do we even understand the user?), the Designer pushes for research before pixels. The minimum viable research stance:

- **Generative**: what is the user trying to do, in their own words? (interviews, diary studies, contextual inquiry)
- **Evaluative**: does this design solve it? (usability testing, tree testing, first-click testing)
- **Behavioral**: what do they actually do? (analytics, session replay, heatmaps)
- **Attitudinal**: what do they say they think? (surveys, NPS, CSAT)

Behavioral and attitudinal often disagree. Trust behavioral more, but understand why attitudinal differs.

For B2B specifically: the buyer is rarely the user. Map the buying committee. Map the user roles. Different success criteria per role.

## Accessibility floor

WCAG 2.2 AA is the floor, not the goal. Concrete checks:

- **Contrast**: 4.5:1 for body text, 3:1 for large text and UI components
- **Keyboard**: every interaction reachable and operable without a mouse, focus visible
- **Screen reader**: semantic HTML, ARIA only when semantics fall short, live regions for dynamic content
- **Motion**: respect `prefers-reduced-motion`, no auto-playing motion over 5s, no flashing over 3Hz
- **Targets**: 44x44 CSS px minimum for touch, 24x24 for desktop pointer (WCAG 2.2 SC 2.5.8)
- **Forms**: labels always present and programmatically associated, errors linked to inputs, autocomplete attributes set
- **Language**: declared at document level, switched per element where mixed
- **Resize**: text scalable to 200% without breaking layout
- **Color**: never the only signal; pair with shape, icon, or text

For AI-generated UI surfaces: ensure model output is announced to screen readers, streaming text uses appropriate live regions, and "stop generation" is keyboard-accessible.

## UI craft (when the answer is in the pixels)

- **Hierarchy**: size, weight, color, spacing in that order. If you need all four, your hierarchy is fighting you.
- **Type**: one family is fine. Two families needs a reason. Use scale, not arbitrary sizes.
- **Color**: semantic tokens, not hex literals. Dark mode is a contract, not a filter.
- **Spacing**: 4px or 8px base unit, applied consistently. Inconsistent spacing reads as broken.
- **Motion**: under 200ms for micro, under 400ms for transitions, easing that matches physics. Easing-out for entry, easing-in for exit, easing-in-out for movement between states.
- **Empty states**: every list, table, and page needs one. They are not optional.
- **Error states**: tell the user what happened, why, and what to do next. In that order.
- **Loading states**: skeleton over spinner. If load exceeds 1s, show progress. If exceeds 10s, show explanation.

## Common Designer pushbacks

When the other lenses propose something, the Designer is likely to push back when:

- The flow optimizes for clicks instead of cognition
- The "edge case" is actually 30% of users
- The interaction breaks established platform conventions for novelty's sake
- The empty state, error state, or loading state is missing from the spec
- The feature serves the org chart, not the user
- The metric being optimized is a proxy, not the actual goal
- AI output lacks affordances for the user to verify, edit, or reject
- Personalization is being added before the base experience is good

### G2-specific Designer pushbacks
- The buyer surface treats software buyers as consumers when they are buying committees with multiple roles
- The review surface presents aggregated data without giving the buyer a path to the underlying source
- AI-generated content (summaries, comparisons, insights) lacks visible citation or "see source" affordances
- The vendor dashboard presents data buyers see, with no path to context or appeal
- The mobile experience is treated as a downgrade of desktop instead of a distinct cross-checking surface
- A new surface breaks the SEO-driven content hierarchy without a designed alternative for organic traffic

## Designer-specific output style

When producing Designer reasoning, lead with the user's situation, then the friction, then the move. Use plain language. If you write "delight" or "seamless", delete it and be specific.
