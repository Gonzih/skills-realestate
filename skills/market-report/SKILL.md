---
name: market-report
description: Generates a professional market conditions report for a specific area — for listing appointments, buyer consults, or client newsletters.
triggers: ["market report", "market analysis", "CMA", "market conditions", "neighborhood market", "real estate market update"]
---

# Market Report

## What this skill does
Creates a polished, professional market conditions report for any area and property type. Outputs a full narrative analysis, a buyer version and seller version of "what this means for you," three agent talking points, and a 200-word newsletter blurb ready for the agent to drop their local MLS numbers into. Built for listing appointments, buyer consultations, and monthly client newsletters.

## How to invoke
/market-report

Claude will ask:
- Area, city, or neighborhood (zip code optional but helpful)
- Property type: single-family (SFR), condo/townhome, multi-family, or all
- Price range focus (e.g., $400K–$600K)
- Purpose: listing appointment, buyer consultation, or client newsletter
- Time period: current month, last 30/60/90 days

## Workflow steps

### Step 1 — Collect inputs
Gather area, property type, price range, purpose, and time period. Note: Claude will generate a framework and narrative structure — the agent fills in actual MLS numbers. Remind the agent which data points to pull: active listings, pending, closed last 30 days, median price, avg DOM, list-to-sale ratio.

### Step 2 — Market narrative
Build the supply/demand story:
- **Inventory framing**: months of supply (< 2 = hot seller's market, 2–4 = balanced-to-seller, 4–6 = balanced, > 6 = buyer's market)
- **Absorption rate**: how fast homes are moving
- **Days on market trend**: rising DOM = softening; falling DOM = heating up
- **List-to-sale ratio**: > 100% = multiple offers common; < 97% = buyers have leverage
- **Seasonal context**: spring surge, summer plateau, fall slowdown, winter quiet — how current conditions compare to seasonal norms

Write this as a coherent narrative paragraph the agent can present, with `[brackets]` where agent inserts real numbers.

### Step 3 — Buyer vs. seller market assessment
Make a clear determination: **Seller's Market / Balanced / Buyer's Market** — with a brief "here's why" in plain language. No hedging. Clients want clarity.

### Step 4 — What this means for clients
Write two separate, distinct paragraphs:

**For sellers**: What the market means for their listing strategy — pricing, timing, days to expect on market, likelihood of multiple offers, negotiating leverage.

**For buyers**: What the market means for their offer strategy — competition level, whether to escalate, contingency negotiability, timeline expectations.

### Step 5 — Agent talking points
Three punchy, memorable talking points the agent can use verbally in the appointment. Format as one sentence each. These should be memorable, quotable, and specific to the market narrative — not generic real estate advice.

Examples of strong talking points:
- "The average home in this price range is spending [X] days on market — that's [faster/slower] than it was six months ago, which tells us [buyers/sellers] have more leverage right now."
- "We're seeing [X]% of homes close above asking price in this neighborhood — that's not luck, that's strategy."

### Step 6 — Newsletter version
200-word client-ready market update. Warm, professional, non-salesy tone. Written in first person from the agent's voice. Structure: opening hook → market summary (with `[number]` placeholders) → what it means → forward-looking note → soft CTA ("Questions about what this means for your home's value? Reply to this email."). Agent drops in actual numbers and sends.

## Example outputs

### Example: South Reno SFR market, $400–600K, listing appointment

**Input:** South Reno, single-family homes, $400K–$600K, listing appointment prep, last 60 days.

**Output:**

**Market Assessment:** Seller's Market (moderate)

**Market Narrative:**
The South Reno single-family market between $400,000 and $600,000 remains firmly in seller's territory, though with some signs of moderation compared to the frenzy of [12–18 months ago placeholder]. Active inventory sits at approximately [X] homes, representing roughly [X] months of supply at the current absorption rate — well below the 4–6 month threshold that would indicate a balanced market. Homes that are priced correctly and show well are going under contract in an average of [X] days, with [X]% closing at or above list price. The list-to-sale ratio of approximately [X]% tells us that sellers still have meaningful leverage, but buyers are becoming more selective, and overpriced listings are sitting longer than they would have a year ago.

**For Sellers:**
This market rewards preparation and strategic pricing. With [X] months of inventory and homes moving in [X] days when priced right, you have a real opportunity — but the window for overpricing and waiting for a buyer has largely closed. Homes that are priced to reflect current comps, staged well, and hit the market at the right time are still receiving strong offers, often multiple. Our strategy will be to price you competitively to generate maximum activity in the first two weeks, which is when your leverage is highest.

**For Buyers:**
Competition at this price point remains real. You're likely to encounter multiple-offer situations on well-priced, move-in-ready homes, and the window between listing and accepted offer is often [X] days or less. That said, the market has softened slightly from its peak — sellers are more open to reasonable inspection contingencies, and escalation clauses, while still useful, don't need to be as aggressive. The most important thing you can do right now is get your financing locked and be ready to move quickly on the right home.

**Talking Points:**
1. "At [X] months of inventory, we're still in seller's market territory — but the buyers showing up right now are serious and qualified, which means the right listing attracts the right offer fast."
2. "Homes priced within 2% of market value are averaging [X] days to contract in this range. Homes priced over that threshold are sitting [X]+ days — the market is very good at punishing wishful pricing."
3. "The list-to-sale ratio in your neighborhood is [X]% — that means sellers are walking away with [X] cents on every dollar of list price, on average."

**Newsletter Version:**
Here's what's happening in the [Area] real estate market this [month].

Inventory in the [$X–$X] price range remains [tight/moderate], with roughly [X] homes actively available and new listings being absorbed in an average of [X] days. [X]% of homes are closing at or above asking price, which tells us that well-priced, well-presented homes are still attracting real competition.

What does this mean for you? If you're thinking about selling, conditions are still favorable — but pricing strategy matters more than ever. The market has little patience for homes that come in too high. If you're buying, come prepared: get pre-approved, know your priorities, and be ready to move when the right home appears.

Looking ahead, [seasonal note — spring inventory typically rises / fall tends to slow things down], so [month] may be [a strong time to list / a good window for buyers to find better selection].

Questions about what this means for your specific situation? Hit reply — I read every one.

[Agent name]
