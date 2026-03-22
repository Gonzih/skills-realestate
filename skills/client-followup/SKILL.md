---
name: client-followup
description: Writes professional, warm follow-up emails and texts for every stage of the client relationship — showings, offers, price reductions, reactivation, and closings.
triggers: ["follow up email", "client follow up", "after showing", "nurture email", "buyer follow up", "seller follow up", "open house follow up"]
---

# Client Follow-Up

## What this skill does
Generates ready-to-send follow-up emails and text messages for every common client scenario. Warm but professional — sounds like a trusted advisor, never a hungry salesperson. Each output includes three subject line options, a 150–200 word email body, a 3–4 sentence SMS version, and a follow-up sequence (day 3 and day 7) if there's no reply. Handles both buyer and seller scenarios.

## How to invoke
/client-followup

Claude will ask:
- Which scenario (see list below)
- Client's name and any personal details to personalize the message
- Key facts: which property, what happened, what you want to happen next
- Tone preference: warm and casual vs. polished and professional

## Workflow steps

### Step 1 — Identify scenario
Choose from the common scenarios below. If the situation doesn't fit, describe it and Claude will adapt:

1. **Post-showing — loved it**: Client was enthusiastic; you want to capture that momentum
2. **Post-showing — didn't love it**: Client was lukewarm; you want to keep them engaged and refine the search
3. **Post-showing — on the fence**: Client is interested but hesitating; you want to help them decide
4. **Offer rejected**: Client's offer wasn't accepted; you need to keep them from walking away
5. **Price reduction conversation**: Seller needs to hear that a price adjustment is necessary
6. **Dormant buyer reactivation**: Buyer went quiet 3, 6, or 12 months ago; you're reaching back out
7. **Post-closing thank you**: Deal is done; time to express gratitude and plant the referral seed
8. **Referral ask**: Standalone message asking a past client for referrals or reviews
9. **Open house follow-up**: Quick follow-up to someone who attended an open house

### Step 2 — Tone calibration
Every message should sound like it came from a trusted advisor, not a salesperson. Guidelines:
- **No pressure language**: avoid "act now," "don't miss out," "this is the one"
- **No hollow phrases**: avoid "just checking in," "touching base," "circling back"
- **Personal and specific**: reference what they actually said, what they saw, what matters to them
- **Confidence without pushiness**: make a clear recommendation, then let them decide

Tone dial: warm and human → professional and polished. Ask agent where on that spectrum they want to land.

### Step 3 — Draft email
Structure:
- **Subject line** (3 options, ranging from casual to professional)
- **Opening**: reference the specific interaction — what they saw, what they said, what happened
- **Body**: deliver value — your take, a recommendation, useful information
- **Soft CTA**: one clear next step, low-pressure ("let me know if you'd like to" not "you need to")
- **Sign-off**: warm and human

Length: 150–200 words. No padding. Every sentence serves a purpose.

### Step 4 — SMS version
3–4 sentences. Sounds like a text from a real person. Same message, compressed. No formal greetings or sign-offs. First name only if appropriate. Ends with a simple question or invitation to reply.

### Step 5 — Follow-up sequence
If no reply in 3 days → gentle nudge, different angle, still no pressure
If no reply in 7 days → final touch, leave the door open, zero guilt-tripping

## Scenarios handled in depth

### After showing — loved it
Lead with their energy. Mirror their enthusiasm without amplifying it into pressure. Offer your honest assessment of the home. Make it easy to say "let's write an offer" without feeling forced.

### After showing — didn't love it
Validate that it wasn't the right fit. Show you listened by acknowledging what didn't work. Pivot: what does this tell us about what they're really looking for? Keep the search alive.

### After showing — on the fence
Name the hesitation without judgment. Offer information that could help them decide (other homes coming, market movement, inspection contingency). Create a low-stakes path forward: "It might be worth a second look" is easier than "let's make an offer."

### Offer rejected
This is the moment clients often walk away. Your job: normalize rejection (it happens to everyone), reframe it as data (now you know what sellers in this market expect), and get them back on offense. No dwelling, no blame, forward momentum.

### Price reduction conversation with seller
This requires the most delicacy. Frame around data, not opinion. The market is talking — you're just translating. Acknowledge that the news isn't what they hoped for. Present the price adjustment as a tool, not a concession. Give them a path forward with a clear recommendation.

### Dormant buyer reactivation
Don't apologize for reaching out. Bring value: something changed in the market, a home came up that matches what they wanted, or rates shifted. Give them a reason to re-engage beyond "just wanted to check in." Respect that life got in the way — no guilt.

### Post-closing thank you + referral ask
This is a two-part message. Part 1: genuine gratitude for trusting you with one of the biggest transactions of their life. Part 2: plant the referral seed naturally — "if anyone you know is thinking about buying or selling, I'd be honored to help them the same way." Don't make them feel obligated.

## Example outputs

### Example: After showing — on the fence

**Input:** Client: Sarah. Showed 4-bed home at 789 Pinecrest Dr. She liked the kitchen and the backyard but worried about the street noise and whether the price was justified. $520K. She said "I need to think about it."

**Output:**

**Subject line options:**
- A: "Thinking about Pinecrest — my honest take"
- B: "789 Pinecrest — a few thoughts after your visit"
- C: "Your thoughts on today's showing"

**Email:**
Hi Sarah,

Thanks for spending time at Pinecrest today — I appreciated your thoughtful questions throughout the showing.

You're right to pause on the street noise. That stretch of road is genuinely busier than most in the area, and it's a real factor. What I'd want you to know is that the insulation in these newer builds does a solid job dampening it once you're inside with windows closed — but only you can decide if that works for your lifestyle.

On the price: the backyard square footage and the 2022 kitchen renovation do justify where they're priced compared to recent sales nearby. That said, there's room to negotiate — this one's been sitting for 19 days, which tells us the seller isn't fielding multiple offers.

If you want a second look before you decide, I can make that happen quickly. Or if there were other concerns I didn't address today, I'm all ears.

No rush — just let me know.

[Agent name]

**SMS version:**
Hey Sarah — still thinking about Pinecrest? Totally fair. The street noise is real, but it's significantly quieter inside — worth knowing. The 19 days on market gives us some negotiating room if you want to explore it. Happy to get you back in for another look or just talk through it — whatever's helpful.

**Day 3 follow-up (no reply):**
Hi Sarah — just wanted to make sure my last note didn't get buried. Pinecrest is still available if you want to revisit, but no pressure either way. Are there other homes from your search list you'd like to schedule? Happy to set up a few showings this weekend.

**Day 7 follow-up (no reply):**
Hi Sarah — I'll keep this short. If Pinecrest isn't the right fit, that's completely okay — it tells us something useful about what you're really looking for. Whenever you're ready to jump back in, I'm here. Feel free to reach out anytime.

---

### Example: Offer rejected

**Input:** Client: Marcus and Jen. Offered $498K on a home listed at $510K. Seller countered at $507K. Clients feel defeated and are talking about "taking a break from looking."

**Output:**

**Subject line options:**
- A: "On the counter — and what I'd do next"
- B: "The seller countered — here's my read"
- C: "Let's talk about the counter on Oak Street"

**Email:**
Hi Marcus and Jen,

I know a counter at $507K isn't the number you were hoping for — and I completely understand the instinct to step back and breathe. That's a normal reaction.

Here's my honest read: a $3K gap after going from $510K to $507K tells me this seller wants to close. They moved. That's meaningful. We're not fighting over philosophy — we're $3,000 apart on a $500K transaction, which comes out to less than $15/month on your mortgage.

My recommendation: come back at $503K and see if they'll split it. If they hold at $507K, you'll have a real decision to make with real information. If they come down, you win.

Taking a break is always an option, and I'll support whatever you decide. But I'd hate to see you step back right when you have leverage.

Want to talk it through? I'm available whenever works for you.

[Agent name]
