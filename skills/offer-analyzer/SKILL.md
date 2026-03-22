---
name: offer-analyzer
description: Analyzes one or multiple offers on a property, scores each on strength and risk, recommends a strategy, and generates a seller-ready presentation.
triggers: ["analyze offer", "review offer", "offer terms", "counter offer", "offer comparison", "evaluate offer"]
---

# Offer Analyzer

## What this skill does
Takes one or multiple purchase offers and produces a structured analysis: a strength score per offer, a risk flag breakdown, a clear recommendation on which to accept or counter, specific counter-offer language, and a one-page offer comparison summary the agent can show the seller. Turns complex contract terms into plain language that empowers sellers to make confident decisions.

## How to invoke
/offer-analyzer

Claude will ask for each offer:
- Offered price and list price
- Earnest money deposit amount
- Down payment percentage and financing type (conventional, FHA, VA, cash, jumbo)
- Contingencies: inspection (yes/no, days), appraisal (yes/no, waived), financing (yes/no, days), sale-of-home contingency
- Proposed close date and how it fits the seller's timeline
- Inclusions or exclusions (appliances, fixtures, furniture)
- Escalation clause details if present (cap, increment)
- Any unusual or non-standard terms

## Workflow steps

### Step 1 — Collect offer details
For each offer, gather all terms above. If comparing multiple offers, label them Offer A, B, C, etc. Ask for the list price and seller's ideal close date to properly contextualize the analysis. If the agent has seller priorities (price vs. certainty vs. timeline), capture those too.

### Step 2 — Strength scoring per offer (1–10 scale)
Score each offer across four dimensions:

**Financial Strength (1–10)**
- 10: All-cash, no financing contingency
- 8–9: 20%+ down, conventional, strong pre-approval
- 6–7: 10–20% down, conventional
- 4–5: FHA/VA (appraisal concerns, longer timelines), < 10% down
- 1–3: Low down payment + financing contingency + sale-of-home contingency

**Certainty of Close (1–10)**
- Deduct points for: financing contingency (–2), inspection contingency with long window (–1), appraisal contingency (–1), sale-of-home contingency (–3), FHA/VA appraisal requirements (–1)
- Add points for: contingency waivers, pre-underwritten approval, strong earnest money

**Timeline Fit (1–10)**
- 10: Close date matches seller's ideal timeline exactly
- Deduct proportionally for each week of mismatch in either direction
- Note: a close that's too fast can be just as problematic as one that's too slow

**Earnest Money Strength (1–10)**
- Benchmark: 1–2% of purchase price is standard; above is strong, below is a flag
- 10: 3%+ of purchase price, released to seller on inspection removal
- 5: 1–2%, standard form
- 1–3: Below 1%, or held in escrow with many release conditions

Produce an **Overall Score** (average of four dimensions) and a one-sentence summary for each offer.

### Step 3 — Risk flags
For each offer, list specific risk factors the seller needs to understand. Flag in plain language:

- **Low earnest money**: Buyer has less financial skin in the game; easier to walk away
- **Long inspection window**: Extended due diligence period prolongs seller's uncertainty
- **Appraisal contingency**: If home doesn't appraise, deal is at risk unless seller reduces price or buyer covers gap
- **Financing contingency**: Deal can fall apart if buyer's loan doesn't close
- **Sale-of-home contingency**: Seller is now dependent on a third transaction they can't control
- **FHA/VA appraisal**: Stricter appraisal standards; appraiser may flag items requiring repair
- **Long close date**: Seller carries the property longer — cost of carry, continued mortgage payments
- **Escalation clause**: Explain clearly how it works and the true effective price
- **Missing items**: Anything not addressed in the offer that should be (possession date, inclusions)

### Step 4 — Recommendation
Make a clear, plain-language recommendation:
- Which offer to accept (and why)
- Which offer to counter (and what to push back on)
- Which offer to decline (and whether to counter first)

If offers are close, explain the trade-off clearly: "Offer A is $8K higher but carries meaningfully more risk. Offer B is cleaner — here's what that's worth to you in practical terms."

Do not hedge. Sellers need a recommendation, not a menu of options with no guidance.

### Step 5 — Counter-offer suggestions
For any offer worth countering, provide:
- **Specific terms to counter**: price, earnest money increase, contingency removal or tightening, close date adjustment
- **Reasonable vs. aggressive**: what's likely to be accepted vs. what might kill the deal
- **Language suggestions**: plain-English counter terms the agent can translate to the contract
- **Walk-away point**: if the buyer doesn't move on X, this deal probably isn't worth pursuing

### Step 6 — Seller presentation
A clean, one-page offer comparison summary formatted for the agent to present to the seller. Layout:

```
OFFER COMPARISON SUMMARY
Property: [Address]   List Price: $[X]   Date: [Date]

                    OFFER A     OFFER B     OFFER C
Offered Price       $           $           $
Over/Under List     +/- $       +/- $       +/- $
Financing           Type        Type        Type
Down Payment        %           %           %
Earnest Money       $           $           $
Close Date          Date        Date        Date
Inspection          Yes/No      Yes/No      Yes/No
Appraisal           Yes/No      Yes/No      Yes/No
Financing Cont.     Yes/No      Yes/No      Yes/No
Sale-of-Home        Yes/No      Yes/No      Yes/No

OVERALL SCORE       X/10        X/10        X/10
```

Followed by a 2–3 sentence recommendation in plain English, written for the seller (not the agent).

## Live Data Sources

### Redfin Public Data Patterns
Redfin exposes structured property and market data through its public pages. Use these patterns to pull comparable sales and validate offer pricing:
- **Sold comps URL pattern**: `https://www.redfin.com/city/{city-id}/{state}/{city}/filter/property-type=house,min-beds={n},max-beds={n},min-sqft={n},max-sqft={n},status=9,include=forsale+mlsonly,sold-3mo`
  - `status=9` = sold; `sold-3mo` filters to last 90 days
  - Extract: sale price, original list price, DOM, price/sqft, sale-to-list ratio
- **Price history**: Each Redfin property page (`/homes/{redfin-id}`) includes a price history timeline — useful for identifying price reductions and re-list events that affect offer valuation
- **Market data by zip**: `https://www.redfin.com/zipcode/{zip}/housing-market` exposes median sale price, sale-to-list ratio, and homes sold above list % for the zip — directly map to the scoring dimensions in Step 2

**Use in offer analysis**: Pull sold comps within 0.5 mile, same bed/bath, closed in last 60 days. Compute median price/sqft. Multiply by subject property sqft to get an independent value estimate. Flag if any offer price is more than 5% above this estimate (appraisal risk) or below (seller may be leaving money on the table).

### Cap Rate Formula with Rentometer Market Rent Data
For investment property offers, compute cap rate to contextualize offer price:

**Cap Rate = Net Operating Income (NOI) / Purchase Price**

Where:
- **Gross Rent**: query Rentometer for market rent estimate
  - Rentometer API endpoint: `https://www.rentometer.com/api/v1/summary?address={encoded_address}&bedrooms={n}&auth_token={key}`
  - Returns: mean rent, median rent, percentile distribution (25th/75th) for comparable rentals within configurable radius
- **Vacancy allowance**: subtract 5–8% of gross rent (use 8% in soft markets, 5% in tight markets)
- **Operating expenses**: use 40–45% of effective gross income as a standard expense ratio for SFR/small multifamily (covers taxes, insurance, maintenance, PM fees — excluding debt service)
- **NOI** = Effective Gross Income × (1 − expense ratio)

**Example query pattern**:
```
GET https://www.rentometer.com/api/v1/summary
  ?address=123+Main+St+Reno+NV
  &bedrooms=3
  &auth_token={key}
```
Use the median rent returned. Apply the formula. Flag if cap rate < 4% (low yield relative to financing cost) or > 8% (either strong deal or elevated risk market — investigate further). Include cap rate in the risk flags section and seller presentation table for investment offers.

## Example outputs

### Example: Two-offer comparison

**Input:**
- List price: $525,000. Seller wants to close by April 15.
- **Offer A**: $530,000. $5,000 earnest money. Conventional, 10% down. Inspection (10 days), appraisal contingency, financing contingency. Close April 10.
- **Offer B**: $515,000. $15,000 earnest money. Conventional, 25% down, pre-underwritten. Inspection (7 days), appraisal waived, no financing contingency. Close April 18.

**Output:**

**Offer A — Score: 6.0/10**
- Financial Strength: 6/10 — Conventional with 10% down is solid but not exceptional
- Certainty of Close: 5/10 — Three contingencies (inspection, appraisal, financing) create three exit doors
- Timeline Fit: 9/10 — April 10 is slightly ahead of seller's ideal date, easy to accommodate
- Earnest Money: 4/10 — $5,000 on a $530K offer is less than 1% — buyer can walk cheaply

*Risk flags: Low earnest money, appraisal contingency (home needs to appraise at $530K), financing contingency. If anything goes sideways, this buyer has multiple ways out with minimal penalty.*

**Offer B — Score: 7.5/10**
- Financial Strength: 8/10 — 25% down, pre-underwritten, strong buyer
- Certainty of Close: 8/10 — No financing or appraisal contingency; inspection window is tight
- Timeline Fit: 8/10 — April 18 is 3 days after seller's target, easily workable
- Earnest Money: 8/10 — $15,000 is nearly 3% — buyer has real money at risk

*Risk flags: $10,000 below list price. Inspection contingency still present (7 days). Minor: close date is 3 days after seller's target.*

**Recommendation:**
Counter Offer B. The $10K price gap is real, but Offer B is significantly cleaner. No appraisal risk, no financing fallout risk, $15K earnest money that actually protects you if the buyer walks. Counter at $522,000 — splitting the difference — and ask for the inspection window to be tightened to 5 days. If they accept, you've traded $8K for a deal that's dramatically more likely to actually close. Offer A's extra price isn't worth the three contingency risks on top of the low earnest money.

**Counter-offer terms for Offer B:**
- Price: $522,000 (from $515,000)
- Earnest money: retain at $15,000 (already strong)
- Inspection: tighten to 5 calendar days
- Close date: request April 15 (seller's target)
- Everything else: accept as written

**Seller Presentation:**

```
OFFER COMPARISON SUMMARY
Property: [Address]          List Price: $525,000

                         OFFER A          OFFER B
Offered Price            $530,000         $515,000
Over/Under List          +$5,000          -$10,000
Financing                Conventional     Conventional
Down Payment             10%              25% (pre-approved)
Earnest Money            $5,000 (<1%)     $15,000 (3%)
Close Date               April 10         April 18
Inspection Contingency   Yes (10 days)    Yes (7 days)
Appraisal Contingency    Yes              WAIVED
Financing Contingency    Yes              NO
Sale-of-Home Cont.       No               No

OVERALL SCORE            6.0 / 10         7.5 / 10
```

**Our recommendation:** Counter Offer B at $522,000 with a 5-day inspection window and April 15 close. Offer B's buyer is significantly stronger — they've already been fully underwritten, they've waived the appraisal contingency, and they have $15,000 at stake if they walk away. The extra $15,000 in Offer A's price comes with meaningful risk: if the appraisal comes in low or their financing hits a snag, you're back on the market. The cleaner deal is often the better deal.
