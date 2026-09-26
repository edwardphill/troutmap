# Trout Species Map

**A global life-list for trout.** Every species and subspecies, mapped by native range, clickable, checkable. Part field guide, part achievement system, part wall art.

> Elder Scrolls completion mechanics × *Trout of the World* × the 50-state quarter map on your grandfather's wall.

**Working domain:** troutspeciesmap.com
**Status:** pre-build spec

---

## 1. The Concept

A user signs in, sees a world map with trout ranges overlaid as translucent watercolor territories, and starts filling it in. Click a territory → species card (illustration, taxonomy, range notes, conservation status). Log a catch → the territory fills in permanently. The map becomes a portrait of where you've been.

No photo uploads. No feed. No social graph. This is a **personal ledger**, not a fishing app.

The paid moment is the **export**: a print-quality rendering of your completed map, dated, with your species list hand-set at the bottom. That's the artifact people actually want.

### What makes it work
- **Finite and knowable.** ~100 entries. You can see the whole board on day one and understand exactly what it would take to fill it.
- **Impossible to complete.** Several entries are extinct (Alvord and Yellowfin cutthroat), several are functionally unreachable. That's a feature — it's what makes 94% mean something.
- **The map is the reward.** Not points. Not a badge. A map.

### What it is not
- Not a catch log with weights, flies, water temps. That's a different product and a crowded one.
- Not a spot-sharing app. Never publish user-entered coordinates.
- Not competitive. See §6 on the honor-system problem.

---

## 2. Species Scope

Target for v1: **~35 headline species, ~95 total entries** across three tiers.

### Tier 1 — *Oncorhynchus* (Pacific & Western North America)

**Cutthroat complex** (*O. clarkii*) — the heart of the American section:

| Subspecies | Range |
|---|---|
| Coastal | *clarkii* — Pacific coast, AK to N. CA |
| Westslope | *lewisi* — MT, ID, BC |
| Yellowstone | *bouvieri* — Yellowstone drainage |
| Snake River finespotted | *behnkei* — upper Snake |
| Bonneville | *utah* — Bonneville basin |
| Lahontan | *henshawi* — NV, E. CA |
| Humboldt | Humboldt drainage, NV |
| Willow–Whitehorse | SE OR / NV border |
| Paiute | *seleniris* — Silver King Creek, CA |
| Colorado River | *pleuriticus* — upper CO basin |
| Greenback | *stomias* — S. Platte / Arkansas |
| Rio Grande | *virginalis* — NM, CO |
| Alvord | **extinct** — Alvord basin, OR/NV |
| Yellowfin | **extinct** — Twin Lakes, CO |

**Rainbow / redband complex** (*O. mykiss*): coastal rainbow, steelhead (anadromous form), Columbia River redband, Great Basin redband, McCloud River redband, Eagle Lake rainbow, Kern River rainbow, Little Kern golden, California golden (*aguabonita*).

**Southwestern & Mexican**: Apache (*O. apache*), Gila (*O. gilae*), Mexican golden (*O. chrysogaster*), plus the undescribed Sierra Madre Occidental forms (Río Yaqui, Río Mayo, Río Conchos, San Pedro Mártir).

### Tier 2 — *Salmo* (Europe, W. Asia, N. Africa)

Brown trout (*S. trutta*) and its recognized relatives and ecotypes: sea trout, ferox, gillaroo, sonaghen (Lough Melvin), marble trout (*S. marmoratus*, Soča), softmouth trout (*S. obtusirostris*, Neretva/Zeta/Krka), Ohrid trout (*S. letnica*) and belvica (*S. ohridanus*), Sevan trout (*S. ischchan*, Armenia), flathead trout (*S. platycephalus*, Turkey), carpione (*S. carpio*, Lake Garda), Adriatic trout (*S. cettii*), and **Atlas Mountain trout** (*S. macrostigma*, Morocco/Algeria) — the only native African trout, and the answer to "what's the African section?"

### Tier 3 — East Asia & Japan

*Oncorhynchus masou* complex: yamame (*masou*), amago (*ishikawae*), biwamasu (Lake Biwa), satsukimasu, Formosan landlocked salmon (*formosanus*, Taiwan).

*Salvelinus* char, if you include them (see below): iwana (*S. leucomaenis*) with its four regional forms — nikko-iwana, yamato-iwana, gogi, ezo-iwana — plus kirikuchi (the southernmost char on earth), Miyabe char, oshorokoma.

### Tier 4 — Char and "trout-adjacent"

**Design decision required.** Brook trout, lake trout, bull trout, and Dolly Varden are *Salvelinus*, not true trout — but every American angler calls them trout, and excluding brook trout would be absurd. Lenok and taimen (*Brachymystax*, *Hucho*, *Parahucho*) are further out still.

**Recommendation:** include them, but in a visually distinct tier with an in-app note explaining the taxonomy. The nerds will respect the honesty and everyone else gets their brookie. Entries: brook trout (+ coaster, salter, aurora forms), lake trout (+ siscowet, humper), bull trout, Dolly Varden, Arctic char, Sunapee/blueback/silver trout, lenok, sharp-snouted lenok, taimen, Sakhalin taimen, Danube huchen, Sichuan taimen.

### The Africa problem — and why it needs a data model, not a hand-wave

Outside the Atlas Mountains, every trout in Africa is introduced: browns and rainbows in Lesotho (Bokong, Malibamatso), Kenya (Aberdares, Mt. Kenya), Tanzania, Zimbabwe, Malawi, and the Cape and Rhodes streams of South Africa. Same story in Patagonia, New Zealand, Tasmania, the Falklands, and half of India (Kashmir, the Nilgiris).

**Every range polygon therefore needs a `status` field:** `native`, `naturalized`, `stocked`, `extirpated`, `extinct`.

This is the single most important schema decision in the project. It drives the map legend, it drives what "complete" means, and it lets you show the same species in two colors on the same map — the brown trout's native European range in one shade and its global introduced range in another. That contrast, rendered well, is the most beautiful thing this site can do.

---

## 3. Art Direction

The reference is watercolor natural-history illustration: soft-edged washes, hand-lettered specimen labels, aged paper, generous margins, one fish centered like a museum plate.

### Legal note — read this before hiring anyone
James Prosek's paintings are under copyright, and *Trout of the World* is his title. "In the style of" is a legitimate aesthetic direction; reproducing his work, tracing it, feeding it to an image model as a reference, or invoking his name in your marketing is not. Keep the influence at the level of **medium and layout**, not composition.

### Where the art actually comes from

1. **Public domain plates — do this first.** Sherman F. Denton's chromolithographs for the New York State Fish, Game and Forest Commission reports (1890s–1900s) are out of copyright, they are watercolor, and they are gorgeous. Covers brook trout, lake trout, brown trout, rainbow. Also check the Bureau of Fisheries reports and the Biodiversity Heritage Library.
2. **Commission the gaps.** ~50 illustrations at $150–400 each = $7.5k–20k. Real money. Phase it: launch with the Denton plates plus a generic silhouette treatment for uncovered species, and commission in batches as revenue allows.
3. **Generated art as placeholder only.** Fine for prototyping the layout. Do not ship it as the paid export — people paying for a print will notice, and it undercuts the entire premise.

### Map style
**Stamen Watercolor** (served through Stadia Maps) is a near-perfect basemap for this and requires zero custom cartography. Overlay range polygons as low-opacity fills with hand-drawn-feeling borders. Hand-lettered display face for headings (Cormorant, Ohno Blazeface, or a licensed script), a clean serif for body.

---

## 4. Range Data — the actual hard part

The map is only as good as the polygons, and the polygons are the part you can't vibe-code.

**Sources:**
- **IUCN Red List** spatial data — best global coverage for freshwater fish. **Free for non-commercial use only; commercial use requires a separate license.** You are planning to sell exports. Resolve this before launch.
- **USGS NAS** (Nonindigenous Aquatic Species) — authoritative for introduced US ranges, public domain.
- **Trout Unlimited** Conservation Success Index / Native Trout range layers — excellent for cutthroat subspecies. Ask permission.
- **State and provincial agency GIS** — the finest-grained cutthroat data exists here, one agency at a time.
- **GBIF** occurrence points — free, CC-licensed, good for generating rough hulls where no polygon exists.
- **FishBase** for taxonomy and native/introduced country lists.

**Realistic approach:** hand-drawn generalized polygons at country/basin resolution for v1, refined over time. You are not building a management tool. A range that is roughly right and beautifully drawn beats a precise one that renders like a GIS export.

**Pipeline:** source data → PostGIS → simplify → generate a single **PMTiles** archive → host on R2 → MapLibre reads it directly. No tile server, no per-request cost, and it keeps your full-precision data off the client (see §5).

---

## 5. Security & Abuse Model

You asked what's missing. This is it.

### Threat 1 — Card testing (the serious one)
A public endpoint that charges $1 is a magnet for carders validating stolen card numbers in bulk. This is not hypothetical; it is the predictable consequence of a cheap, unauthenticated charge endpoint. If it happens you eat authorization fees, dispute fees, and possibly a Stripe account review.

**Mitigations, all of them:**
- **Stripe Checkout (hosted)** rather than a custom form — moves PCI surface and much of the fraud tooling onto Stripe.
- **Stripe Radar** on, with rules for velocity by IP, email domain, and card fingerprint.
- **Cloudflare Turnstile** challenge *before* you create a PaymentIntent — never expose PaymentIntent creation to an unchallenged request.
- **Hard rate limits:** N payment attempts per IP per hour, per email per day. Fail closed.
- **Email verification before payment.** Verified address → then checkout. Kills scripted volume cheaply.
- **Block disposable email domains** at signup.

### Threat 2 — The $1 unit economics
Stripe takes 2.9% + $0.30. A $1 charge nets **$0.67** — a 33% take rate. Worse, a single chargeback costs ~$15, wiping out 22 signups.

**The $1 is not revenue, it's an identity tax** — and that's a legitimate pattern. But consider:
- **$5 one-time** nets $4.55 (9% fee), is an equally strong bot deterrent, and is still an easy yes for the target user.
- Or **free account, paid export** — zero signup friction, monetize the moment someone actually wants something.
- Or **$1 signup credited toward the first export.** Preserves the anti-bot gate and the good-faith framing.

Whatever you choose: clear billing descriptor (`TROUTSPECIESMAP.COM`), instant emailed receipt, and a no-questions refund link in that email. Cheapest chargeback prevention available.

### Threat 3 — Data scraping
Your range polygons are the crown jewels and a `fetch()` away if you ship raw GeoJSON.
- Serve **simplified, tiled** geometry only. Keep full precision server-side.
- Rate limit tile and API requests per session.
- Watermark exports; embed a per-user identifier in export metadata.
- Species metadata behind auth, not in the initial page payload.

### Threat 4 — Automated account creation / agent abuse
With no photo uploads and no public UGC, the blast radius is small — mostly database bloat. The payment gate plus Turnstile handles nearly all of it. Add:
- **Passkeys or magic links, no passwords.** Eliminates credential stuffing and password reuse entirely.
- Per-account write limits (a human logs a handful of species a week, not 400 a minute).
- Anomaly flag on accounts that complete >50% of the list within an hour of signup.

### Threat 5 — Export abuse
- Render **server-side**, queue it, cap at N exports per user per month.
- Deliver via **short-lived signed URLs**. Never expose the storage bucket.
- Idempotency keys so a double-click doesn't render twice.

### Baseline hygiene
Cloudflare WAF and bot management in front of everything. Row-level security on the database so a user can only ever read their own log. Strict CSP. All secrets in the platform's secret store, never in the repo. Structured logging with alerts on payment-failure spikes.

### Privacy
You are collecting where people fish. Some of these are sensitive, low-density, protected populations. **Never store user-entered coordinates at finer resolution than you display**, never expose another user's locations, and say so plainly on the marketing page. It's both correct and a real differentiator.

---

## 6. The Honor-System Problem

No photo upload means no verification. Be deliberate about it:

- **Ship no global leaderboard.** A ranked list of unverifiable claims is worthless and invites gaming.
- Frame the whole thing as a **personal life list**, like a birder's notebook. Honesty is the point; the only person you can cheat is yourself.
- If you ever want verification, the lightweight path is an **optional photo attached privately to a log entry**, never published, used only to unlock a "verified" mark on the export. Opt-in, and a v2 decision.

---

## 7. Feature Set

**v1 (launch)**
- Interactive world map, range polygons by species, native/introduced toggle
- Species detail cards: illustration, scientific and common names, range notes, IUCN status, a short essay
- Auth (magic link or passkey) + payment gate
- Log a catch: species, date, optional water name, optional private note. Marks the territory complete.
- Progress: % complete overall, by genus, by continent
- Paid map export (PNG + print-resolution PDF)

**v2**
- Regional challenges mirroring real programs (Western Native Trout Challenge, Utah Cutthroat Slam)
- Rarity tiers and completion milestones
- Physical print fulfillment via a POD partner
- Species essays from guest writers
- Optional private verification photos

**Explicitly out of scope**
- Social feed, comments, following
- Spot sharing
- Weather, flow data, hatch charts
- Mobile apps (responsive web is sufficient)

---

## 8. Recommended Stack

Chosen for one-shot buildability: boring, well-documented, heavily represented in training data.

| Layer | Choice | Why |
|---|---|---|
| Framework | **Next.js (App Router)** | Densest documentation of any option; server actions keep data access off the client |
| Hosting | **Vercel** | Zero-config; free tier covers launch |
| Database | **Neon** or **Supabase** (Postgres + PostGIS) | PostGIS is non-negotiable for range geometry |
| Auth | **Clerk** or **Supabase Auth** | Passkeys and magic links built in; bot protection included |
| Map | **MapLibre GL JS** | Open source, no Mapbox billing surprises |
| Basemap | **Stadia Maps (Stamen Watercolor)** | The aesthetic, for free, immediately |
| Tiles | **PMTiles on Cloudflare R2** | Single-file vector tiles, no tile server, no egress fees |
| Payments | **Stripe Checkout + Radar** | Hosted flow, minimal PCI surface |
| Export render | **Satori + resvg**, or Puppeteer | Server-side, deterministic |
| Email | **Resend** or **Postmark** | Magic links and receipts |
| Edge | **Cloudflare** (WAF, Turnstile, rate limiting) | Every §5 mitigation in one place |

### Schema sketch

```
species        id, scientific_name, common_name, genus, tier,
               iucn_status, illustration_url, essay_md, is_extinct
ranges         id, species_id, geometry(MultiPolygon, 4326),
               status(native|naturalized|stocked|extirpated|extinct),
               source, source_license
users          id, email, created_at, paid_at, export_credits
catches        id, user_id, species_id, caught_on, water_name,
               note, created_at            -- no coordinates stored
exports        id, user_id, status, storage_key, created_at, watermark_id
```

---

## 9. Build Approach

**Do not one-shot the whole thing.** Not because the model can't — because "one shot" collapses three genuinely separate problems into one prompt and you'll get a mediocre version of all three.

Split it:

1. **Data first, alone.** Build the species list and range polygons as a standalone dataset before any UI exists. This is the part that takes weeks and the part no model can shortcut, because the source data is scattered across agency GIS portals and paywalled licenses. Get it into PostGIS and validate it renders.
2. **App shell — one shot this.** Auth, payments, schema, map viewer, species cards, logging, progress. This is well-trodden CRUD-plus-a-map and a capable model will produce a working version from a detailed prompt in a single pass. Feed it this document.
3. **Export renderer — separate.** Its own pass. Print-quality output has fiddly requirements (bleed, DPI, CMYK, font embedding) that will pollute the main build if mixed in.
4. **Security hardening — separate pass.** Go through §5 line by line against the running app. Security added as an afterthought in a feature prompt is security that doesn't exist.
5. **Art last.** It's the longest lead time and it blocks nothing technical.

### Which model

For step 2, **Claude Opus 5** is the right default — this is a well-understood stack, and the constraint is spec quality, not model capability. **Claude Fable 5.1** is worth the premium for the initial architecture pass on step 3 (the export renderer, where the failure modes are subtle) and for step 4. **Sonnet 5** for iteration once the shape is set.

Run it through **Claude Code** rather than chat — it reads and writes the whole repo, runs the dev server, and can iterate against actual errors. On a Max subscription this is flat-rate; via API, a project this size lands in the low hundreds of dollars across all four steps.

---

## 10. Costs

### Build
| Item | Cost |
|---|---|
| Domain (Cloudflare Registrar, at-cost) | ~$11/yr |
| Claude Max subscription, 2 months | $200–400 |
| — or API tokens instead | ~$150–400 total |
| Illustrations (50 commissioned @ $150–400) | $7,500–20,000 |
| Illustrations (public-domain plates first) | **$0** |
| Range data licensing (if IUCN commercial) | TBD — inquire early |
| **Realistic launch total, PD art route** | **~$250–450** |

### Running (monthly)

| Service | At launch | At ~10k users |
|---|---|---|
| Vercel | $0 (Hobby) | $20 (Pro) |
| Neon / Supabase | $0 | $19–25 |
| Cloudflare R2 + WAF | $0–5 | $5–20 |
| Stadia Maps | $0 (200k credits) | ~$20 |
| Clerk | $0 (<10k MAU) | $25 |
| Resend | $0 (3k emails) | $20 |
| **Total** | **~$0–5** | **~$110–130** |

Stripe is variable: 2.9% + $0.30 per transaction.

### Break-even
At $5 one-time (nets $4.55), roughly **25 signups/month** covers infrastructure at scale. At $1 (nets $0.67), you need ~170. That gap is the argument for $5, or for free-signup-plus-paid-export.

---

## 11. Domain

**troutspeciesmap.com** — nothing currently resolves there in search results, but that is not a registration check. Verify at a registrar before doing anything else.

Register at **Cloudflare Registrar** (~$11/yr, sold at wholesale with no markup and no renewal games) since you'll be on Cloudflare anyway.

Note that **troutmap.com is taken** — an existing waterproof-river-map business. Different product, but avoid marketing collisions.

**Backups to check in the same session:** troutlifelist.com, troutoftheworld.com (likely conflicts with the Prosek title — avoid), thetroutmap.com, salmonidae.com, troutslam.com, worldtroutmap.com.

Grab the matching handles on Instagram and Bluesky at the same time. Free, and you'll want them.

---

## 12. Open Questions

1. Char in or out? (Recommendation: in, visually separated.)
2. $1 vs $5 vs free-with-paid-export?
3. Does the export sell as a digital file, a physical print, or both?
4. What counts as "caught" — the species, or every subspecies with contested taxonomy?
5. Is the introduced-range layer part of completion, or display-only? (Recommendation: display-only. A brown trout in Patagonia shouldn't tick the same box as one in the Neretva.)
6. IUCN commercial licensing — resolve before charging for anything that renders their polygons.
