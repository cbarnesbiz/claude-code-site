# PRD: Claude Code ROI Calculator

## Overview

An interactive calculator embedded on the Claude Code landing page that shows PMs and PMMs how much time they'd save per week by using Claude Code. The calculator takes inputs based on tasks our target buyer already does, shows a personalized time-saved estimate, and converts skeptics by making the value concrete and specific to their workflow.

## Target User

Series B SaaS PMM, 3-5 years experience (see `persona.md`). Uses ChatGPT daily but hasn't tried AI coding tools. Skeptical that coding tools are relevant for non-engineers. Cares about pipeline contribution, competitive intel, and content velocity.

The calculator must speak entirely in this buyer's language. No mentions of repos, commits, PRs, builds, or engineering workflow.

## Goals

1. **Convert skeptics** - Give the "this isn't for me" PMM a personal, quantified reason to try Claude Code
2. **Drive sign-ups** - Calculator output ends with a CTA to get started
3. **Collect signal** - Input values tell us which pain points resonate most (useful for future messaging and sales)

## User Flow

1. User lands on calculator section (or navigates to it from the main page)
2. User adjusts 4-5 sliders representing hours spent per week on specific tasks
3. Calculator displays time saved per week, per month, and per quarter in real time
4. Results section reframes time saved as tangible outcomes (extra campaigns, pages shipped, etc.)
5. CTA prompts user to try Claude Code

## Inputs

Each input is a horizontal slider with a label, description, and hours-per-week value (0-10 range, 0.5 hr increments).

| Input | Label | Description | Default |
|-------|-------|-------------|---------|
| 1 | Competitive research & updates | Tracking competitor positioning, pricing changes, and updating comparison pages | 3 hrs |
| 2 | Writing & editing content | Drafting landing pages, one-pagers, case studies, and sales enablement materials | 4 hrs |
| 3 | Requesting site changes | Filing tickets, writing briefs, and waiting on engineering for website copy edits, new pages, or content updates | 3 hrs |
| 4 | Building presentations & prototypes | Creating pitch decks, campaign mockups, and quick prototypes to pitch internally | 2 hrs |

## Time-Saved Assumptions

These multipliers represent the estimated portion of each task that Claude Code can accelerate or eliminate. They should be conservative to maintain credibility with a skeptical audience.

| Input | Time saved | Rationale |
|-------|-----------|-----------|
| Competitive research & updates | 50% | Claude Code can pull in competitor data, generate comparison tables, and publish updated pages directly |
| Writing & editing content | 40% | Drafting and formatting is faster; PMM still reviews and refines (this feels honest to a ChatGPT user who knows AI doesn't replace judgment) |
| Requesting site changes | 80% | This is the biggest unlock: most small-to-medium site changes can be done directly, eliminating the ticket-and-wait cycle entirely |
| Building presentations & prototypes | 30% | Claude Code can scaffold prototypes and generate content, but presentation design still requires manual work |

## Output Display

### Primary metric
- **Hours saved per week** - large, prominent number (e.g., "6.5 hrs/week")
- **Hours saved per month** - weekly number x 4
- **Hours saved per quarter** - weekly number x 13

### Outcome reframe
Translate raw hours into outcomes the persona cares about. Display 2-3 of these dynamically based on which inputs have the highest values:

- "That's **X extra landing pages** you could ship per quarter" (if content + site changes inputs are high)
- "That's **X more competitive updates** per month while they're still fresh" (if competitive research input is high)
- "That's **X fewer engineering tickets** filed per month" (if site changes input is high)
- "That's nearly **a full extra day per week** back on strategy" (if total hours saved >= 6)

### CTA
Below the results: "Get those hours back." with a primary button linking to Claude Code sign-up.

## Design Requirements

- Inline on the existing landing page, added as a new section between "Real Talk" and "The Bottom Line"
- Matches existing site styling: same fonts, colors, card treatment, amber/orange accent palette
- Sliders use the amber/orange gradient for the filled track
- All calculations happen client-side in vanilla JS (no frameworks, no dependencies)
- Fully responsive: sliders stack vertically on mobile
- Results update in real time as sliders move (no submit button)
- Animations: results numbers should count up/down smoothly when values change

## What's Out of Scope

- Email capture or gating (keep it frictionless; don't gate the value)
- Backend or analytics integration (can be added later)
- Comparison to other tools or competitors
- Pricing or cost calculations (this is about time, not money)

## Success Metrics

- **Engagement:** % of page visitors who interact with at least one slider
- **Completion:** % of visitors who scroll past the calculator results
- **Conversion:** Click-through rate on the calculator CTA vs. the existing page CTAs

## Open Questions

1. Should we let users input their hourly rate or salary band to convert time saved into dollar value? (Risk: feels salesy and may break trust with a skeptical buyer. Recommendation: leave it out for v1.)
2. Should the calculator be a standalone page or a section on the main page? (Recommendation: section on the main page for v1, with option to link to it directly via anchor.)
3. Do we want to persist input values in localStorage so returning visitors see their previous inputs? (Nice-to-have for v2.)
