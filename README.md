# skills-realestate

Four AI skills for real estate agents using Claude Code. One install drops them all into `~/.claude/skills/` and makes them invocable as slash commands.

Part of the **EcoFiClaw** professional skills ecosystem.

## Install

```bash
npx @gonzih/skills-realestate
```

Then restart Claude Code. All four skills are ready.

**Manual install:** Copy any `skills/<skill-name>/SKILL.md` to `~/.claude/skills/<skill-name>/SKILL.md`.

---

## The 4 skills

### /listing-writer
**Write MLS listings and marketing copy from property specs.**

Give Claude the basics — beds, baths, sqft, key features, price, target buyer — and get back:
- A punchy 150-word MLS description
- A narrative 400-word website/marketing version
- Three Instagram captions with hashtags

Trigger phrases: *listing description, write listing, property description, MLS listing, listing copy*

---

### /market-report
**Generate a professional market conditions report for any area.**

Input an area, property type, price range, and whether this is for a listing appointment, buyer consult, or newsletter. Get back:
- A market narrative with supply/demand analysis (you fill in your MLS numbers)
- A buyer's market / seller's market determination with reasoning
- Separate "what this means for you" sections for buyers and sellers
- Three talking points for your live presentation
- A 200-word client newsletter blurb, ready to send

Trigger phrases: *market report, market analysis, CMA, market conditions, neighborhood market, real estate market update*

---

### /client-followup
**Write warm, professional follow-up emails and texts for every client scenario.**

Tell Claude the scenario and the client details. Get back:
- Three subject line options
- A 150–200 word email (warm but never pushy)
- A 3–4 sentence SMS version
- Day-3 and day-7 follow-up messages if there's no reply

Scenarios covered:
- After a showing (loved it / didn't love it / on the fence)
- After an offer is rejected
- Price reduction conversation with a seller
- Reactivating a buyer who went quiet 3–12 months ago
- Post-closing thank you with referral ask
- Open house follow-up

Trigger phrases: *follow up email, client follow up, after showing, nurture email, buyer follow up, seller follow up, open house follow up*

---

### /offer-analyzer
**Analyze offers, score their strength, flag risks, recommend a counter strategy, and build a seller presentation.**

Input the offer terms — price, earnest money, down payment, financing type, contingencies, close date. Get back:
- A 1–10 strength score per offer across four dimensions
- Risk flags in plain English
- A clear recommendation (not a menu of options — an actual recommendation)
- Specific counter-offer terms with what's reasonable vs. aggressive
- A one-page offer comparison table to show the seller

Works for single offers and multi-offer situations.

Trigger phrases: *analyze offer, review offer, offer terms, counter offer, offer comparison, evaluate offer*

---

## Who this is for

Real estate agents who use Claude Code or Claude via Telegram and want AI that understands their workflow — not generic AI that needs to be re-educated every session. These skills encode the professional knowledge so Claude can act like a skilled transaction coordinator and marketing partner from the first message.

## License

MIT
