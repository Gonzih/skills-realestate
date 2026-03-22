---
name: listing-writer
description: Produces a compelling MLS-ready property listing from basic specs — two versions (MLS 150 words, marketing 400 words) plus Instagram captions.
triggers: ["listing description", "write listing", "property description", "MLS listing", "listing copy"]
---

# Listing Writer

## What this skill does
Transforms raw property specs into emotionally compelling listing copy that moves buyers to act. Generates three deliverables: a punchy 150-word MLS listing, a narrative 400-word marketing description for your website, and three Instagram caption options with hashtags. Every listing opens with a lifestyle hook and closes with urgency.

## How to invoke
/listing-writer

Claude will ask:
- Address or area (city/neighborhood is fine if you want privacy)
- Bedrooms, bathrooms, square footage, lot size, year built
- Key features: kitchen update, pool, views, garage, bonus rooms, outdoor space
- Neighborhood highlights: schools, walkability, proximity to amenities
- Asking price and target buyer profile (first-time buyer, family, investor, luxury)

## Workflow steps

### Step 1 — Collect specs
Gather all property details from the agent. If anything is missing, ask before writing. Required: bed/bath/sqft, price range, at least 3 standout features. Optional but valuable: year built, lot size, recent updates, HOA, school district, neighborhood vibe.

### Step 2 — Emotional hook
Identify the #1 lifestyle benefit this property delivers. Pick one:
- **Entertainer's dream** — open floor plan, outdoor kitchen, pool, great room
- **Move-in ready family home** — updated systems, good schools, flex spaces
- **Investor opportunity** — duplex, ADU potential, strong rental market
- **Luxury retreat** — views, high-end finishes, private lot, resort amenities
- **Urban lifestyle** — walkability, transit, lock-and-leave convenience

This hook anchors the emotional opening of both versions.

### Step 3 — MLS version (150 words)
Structure:
1. One-sentence punchy opener using the emotional hook
2. 3 key features with specific details (not generic — "quartz waterfall island" not "updated kitchen")
3. Outdoor/lot highlight
4. Neighborhood/location sentence
5. Call to action: "Schedule your showing before this one's gone."

Target: agents scanning MLS. Every word earns its place.

### Step 4 — Marketing version (400 words)
Structure:
1. Opening paragraph (3-4 sentences): paint the lifestyle picture
2. Interior tour: living spaces, kitchen, primary suite, secondary rooms — lead with the best
3. Outdoor living: backyard, views, curb appeal
4. Neighborhood paragraph: schools, shops, commute, community feel
5. Closing vision: who this home is perfect for and why they'll love it
6. Soft CTA: "Homes like this don't wait — reach out today to arrange a private tour."

Target: buyers browsing Zillow/website at 11pm. Make them feel it.

### Step 5 — Social captions
Three Instagram caption options:
- **Option A**: Story-led, 3-4 sentences, personal and warm
- **Option B**: Feature-forward, bullet-style with emojis
- **Option C**: Short and punchy, 1-2 sentences, strong hook

Each followed by 10-12 relevant hashtags mixing broad (#realestate, #justlisted) and local (#RenoRealEstate, #NVhomes).

## Live Data Sources

### Zillow Public Data
Zillow exposes property data through its public-facing pages and bridge data partnerships. Use the following patterns when enriching a listing:
- **Property details**: `https://www.zillow.com/homes/{address}_rb/` — scrape or use Zillow's Bridge Interactive data feed (for MLS-connected agents) to pull current Zestimate, recent sold comps, and days on market history.
- **Comparable sales query pattern**: Search `https://www.zillow.com/homes/recently_sold/{zip-code}_rb/` filtered by bed/bath/sqft range and sold within 90 days. Pull: address, sale price, price/sqft, DOM, and list-to-sale ratio.
- **Neighborhood data**: Zillow's neighborhood pages (`/neighborhood/{city}/{neighborhood}/`) expose median listing price trends, inventory count, and price-per-sqft history — useful for the neighborhood paragraph in the marketing version.

### Walk Score API
API documentation: `https://www.walkscore.com/professional/api.php`
- **Endpoint**: `https://api.walkscore.com/score?format=json&address={encoded_address}&lat={lat}&lon={lon}&transit=1&bike=1&wsapikey={key}`
- **Returns**: Walk Score (0–100), Transit Score, Bike Score, and a plain-English description (e.g., "Walker's Paradise", "Car-Dependent").
- **Query pattern**: Geocode the property address first (Google Maps Geocoding API or free Nominatim), then pass lat/lon + address to Walk Score. Cache results — scores change infrequently.
- **Use in listing copy**: Embed Walk Score in the neighborhood paragraph ("Walk Score of 82 — most errands on foot") and Instagram captions for urban/suburban properties where walkability is a selling point.

### GreatSchools API — School Ratings
- **Endpoint**: `https://api.greatschools.org/schools/nearby?key={key}&state={state}&lat={lat}&lon={lon}&radius=2&limit=5&levelCode=e,m,h`
- **Returns**: School name, type (public/private/charter), level (elementary/middle/high), GreatSchools rating (1–10), distance in miles.
- **Query pattern**: Pass property lat/lon with a 2-mile radius. Filter for `levelCode=e,m,h` to get all three levels. Sort by rating descending to surface the strongest schools.
- **Use in listing copy**: Reference the top-rated school by name and rating in both MLS and marketing versions. Example: "Zoned for Damonte Ranch High (GreatSchools: 8/10)." Always note if ratings are based on test scores vs. equity factors.

## Example outputs

### Example: Mountain view home in Reno, NV

**Input:** 3 bed / 2 bath, 1,820 sqft, 0.18 acre lot, built 1998. Renovated kitchen (2022, quartz counters, new appliances), mountain views from backyard, 2-car garage, new HVAC. South Reno, Damonte Ranch area, great schools. Asking $485,000. Target: families and move-up buyers.

**Output:**

**MLS Version (148 words):**
Mountain views and a fully renovated kitchen in one of South Reno's most sought-after neighborhoods — welcome home. This 3-bedroom, 2-bath Damonte Ranch gem packs 1,820 sqft of smart, livable space with fresh quartz counters, stainless appliances, and an open layout built for how families actually live. The new HVAC (2022) means comfortable year-round living with zero surprises. Step out back and wake up to those Sierra views every morning — no neighbors behind, just sky and mountains. Two-car garage, great storage, and a neighborhood known for top-rated schools and tight-knit community round out the picture. Walking distance to parks and shopping, minutes from the freeway. Move-in ready, priced right, and the kind of listing that goes fast. Schedule your showing before this one's gone.

**Marketing Version (opening paragraph):**
There's a moment every morning in this home — coffee in hand, looking out at the Sierra Nevada from your own backyard — where you realize this is exactly the life you were working toward. Set on a quiet street in Damonte Ranch, one of South Reno's most established family neighborhoods, 123 Mountain View Lane delivers the complete picture: a gut-renovated kitchen that makes cooking feel like a pleasure, a layout designed for real life, and the kind of peace and permanence that comes from knowing you found the right one.

**Instagram Caption A:**
Mountain views. Renovated kitchen. One of Reno's best school districts. This Damonte Ranch beauty just hit the market at $485K and it's not going to last. Three beds, two baths, 1,820 sqft of move-in-ready living — reach out if you want to see it before the weekend. 🏔️

#RenoRealEstate #DamonteRanch #JustListed #NVHomes #MountainViews #RenovatedKitchen #SouthReno #MoveInReady #RenoHomes #NevadaRealEstate #HomeBuying #RealtorLife
