# G1-Fun Coverage Audit & Plan

Date: 2026-05-09. Audited `index.html` (1420 lines) against research files 01–03.

## Phase 1 — Coverage punch list

### CRITICAL gaps (will cost real test points)

1. **Child car seat stages** — fully missing. Stages (rear-facing → forward → booster → seatbelt) are tested. Reachable via Q: "When does a child exit the booster stage?" → answer is age 8 / 36 kg / 145 cm, ANY one of the three.
2. **HOV lane rules** — fully missing. Asked: "min occupants for HOV" (2+) and the green-plate EV exemption. Also `HOV diamond` pavement marking.
3. **Lending your licence is illegal** — MTO official sample-test question. Page never mentions it.
4. **Impaired-driving thresholds for full-G drivers** — page only says "G1 = 0.00". Test asks about warn range (0.05–0.079 → 3-day suspension) vs criminal (0.08+). Currently invisible.
5. **Pavement markings beyond yellow/white** — research file 02 explicitly calls out: continuity lines, bike box, HOV diamond, two-way left turn lane (TWLTL), crosswalk markings. Page only has the yellow/white callout. MTO sample test asks about continuity lines + arrows.
6. **Slow-Moving Vehicle triangle** (orange triangle w/ red border) — not in sign gallery; topic checklist explicitly calls it out.
7. **Police directions override traffic signals** — mentioned only in tl;dr cheat sheet bullet. Should be a real "rule" item the user encounters during studying, not a buried bullet.
8. **School bus must stop at every railway crossing** — MTO sample-test fact (file 03 Q&A). Missing.

### NICE-TO-HAVE (partial / low-stakes)

- Train stopping distance (~2 km) — atmospheric, but useful pull quote.
- Speed-fine $/km tiers — too granular for this page.
- Pennant no-passing zone sign — file 02 mentions it; rare on test.
- Volunteer responder green flashing lights — rare.
- 150m no-follow rule for fire/ambulance — rare.
- Commercial-vehicle 120m following distance — out of G1 scope.
- Demerit reaccumulation 6-month suspension detail — already implied.

### SKIP (out of scope or already strong)

- BAC for commercial drivers, ignition interlock specifics, criminal-court fines — beyond G1 written test.
- Stunt driving conviction tiers ($2k–$10k by repeat) — page's existing card is enough.
- Snow whiteout / pull-off advice — covered by existing weather card.
- G2 passenger restrictions — page is about G1; skip per scope.

### Already verified present (no action needed)

Default speed trio · 2/3/4-sec following · 30m/150m signal distances · school bus amber/red/20m/divided · PXO + 30m no-pass · 4-way stop tie · roundabout · yellow vs white lines · solid/broken passing · 5m rail + 30m stalled · full traffic light glossary · lane control X/arrow · sign shapes (octagon/triangle/diamond/orange/pentagon/circle/crossbuck) · G1 restrictions · demerit thresholds 9/15 · stunt thresholds · novice distracted 30/90/cancel · move-over · $2k collision · cyclist 1m · truck blind spots · skid · hydroplane · black ice / fog low-beam · 3/9/15m parking · hill wheel direction · tread 1.5mm · mirror 5s · headlight 150m · eye test/ID/fee/age/retake/BDE.

---

## Phase 2 — Draft additions

Total: **8 additions** (well under "~40% bloat" budget). All slotted inside existing tabs/sections; no new sections.

### 1. Child car seat stages → `#tab-behaviour` card-grid (after the "tires" card)

INSERT before the closing `</div>` of `<div class="tab-panel" id="tab-behaviour">` (or after `<div class="card">`…trucks card).

Anchor: insert AFTER the "trucks" card `<div class="card"><span class="tag">trucks</span>…</div>`.

```html
      <div class="card rose">
        <span class="tag">car seat stages</span>
        <h3>The kid-seat ladder</h3>
        <table class="lil"><tr><th>kid</th><th>seat</th></tr>
        <tr><td>≤9 kg (infant)</td><td>Rear-facing</td></tr>
        <tr><td>9–18 kg (toddler)</td><td>Forward-facing</td></tr>
        <tr><td>18–36 kg, &lt;145 cm, &lt;8 yr</td><td>Booster</td></tr>
        <tr><td>Hits ANY of: 36 kg / 145 cm / 8 yr</td><td>Regular belt</td></tr></table>
        <p class="pull">Booster exit = ANY one of the three thresholds, not all.</p>
        <p>Never put a rear-facing seat in front of an active airbag.</p>
      </div>
```

### 2. HOV lane card → `#tab-rules` card-grid (after "railway crossings" card)

Anchor: insert AFTER the railway crossings card (last card in tab-rules), before the closing `</div></div>` of tab-rules.

```html
      <div class="card mint">
        <span class="tag">HOV lanes</span>
        <h3>Min 2 humans (or a green plate)</h3>
        <p>HOV = High-Occupancy Vehicle. You need <strong>at least 2 people</strong> in the car to use it.</p>
        <p>Exception: <strong>green-plate</strong> EVs and plug-in hybrids can use HOV solo. Buses + emergency vehicles always allowed.</p>
        <p>Open 24/7 unless posted. Cross only at the dashed entry/exit gaps. Misuse = <strong>3 demerits</strong>.</p>
      </div>
```

### 3. Lending licence + police-override card → `#tab-g1rules` card-grid (after "timeline" card)

Anchor: insert AFTER the "timeline" card (last in tab-g1rules), before its closing `</div></div>`.

```html
      <div class="card cherry">
        <span class="tag">two test favourites</span>
        <h3>Two random rules they LOVE</h3>
        <p>1. <strong>Never lend your licence.</strong> To anyone. Ever. It's illegal full-stop. (MTO sample-test classic.)</p>
        <p>2. If a <strong>police officer</strong> is directing traffic and the signal disagrees with them — <strong>obey the cop</strong>. Officers override every sign and light.</p>
      </div>
```

### 4. Full-G BAC card (warn vs criminal) → `#tab-penalties` card-grid (after "the $2,000 collision rule" card)

Anchor: insert AFTER the `$2,000 collision rule` card, before the closing `</div></div>` of tab-penalties.

```html
      <div class="card ink">
        <span class="tag">BAC for everyone else</span>
        <h3>Full-G drinking limits (FYI tier)</h3>
        <p>You're zero, but the test sometimes asks about full-G:</p>
        <p>· <strong>0.05–0.079</strong> = "warn range" → roadside 3-day suspension + $250</p>
        <p>· <strong>0.08+</strong> = Criminal Code offence → 90-day roadside + 7-day impound</p>
        <p class="pull">G1/G2/M1/M2/under-22 = always 0.00, no warn range.</p>
      </div>
```

### 5. Pavement markings deep-dive card → `#signs` section, after the existing pavement-line callout

Anchor: insert AFTER `<div class="callout" style="margin-top:2.5rem"><strong>Pavement-line rule:</strong>…</div>` (around line 989-991), before the `<h3>traffic light glossary` heading.

```html
  <h3 style="font-family:'Bagel Fat One',cursive;font-size:1.6rem;margin:2.5rem 0 .8rem">painted-on-the-road extras 🛣</h3>
  <div class="card-grid">
    <div class="card yolk">
      <span class="tag">continuity lines</span>
      <h3>Wider, closer-spaced white dashes</h3>
      <p>Means your lane is <strong>ending or exiting</strong>. Change lanes if you want to keep going straight. They're a warning, not an invitation.</p>
    </div>
    <div class="card mint">
      <span class="tag">two-way left turn lane</span>
      <h3>The shared middle lane</h3>
      <p>Centre lane bordered by <strong>double yellow + a broken yellow inside</strong>, with left-arrows in both directions. Either side uses it to <em>stage</em> a left turn — never to drive in.</p>
    </div>
    <div class="card cherry">
      <span class="tag">bike box</span>
      <h3>Don't sit in the painted box</h3>
      <p>Box w/ a bike symbol at the intersection = bike waiting area. Cars stop <strong>behind</strong> it. Bikes get to slot in front for the green.</p>
    </div>
    <div class="card rose">
      <span class="tag">HOV diamond + arrows</span>
      <h3>Pavement tells you the rules</h3>
      <p>White ◇ painted on the road = HOV lane. White arrows in a lane = you can only go that direction. Crosswalk = two parallel white lines; PXO adds a giant X in each lane.</p>
    </div>
  </div>
```

### 6. Slow-Moving Vehicle sign → `#signs` `.sign-gallery`, after "No U-Turn" sign

Anchor: insert as a NEW `<div class="sign">` AFTER the "No U-Turn" sign (last in gallery).

```html
    <div class="sign">
      <svg viewBox="0 0 100 100"><polygon points="50,14 86,80 14,80" fill="#d4291f" stroke="#1a140f" stroke-width="3"/><polygon points="50,28 74,72 26,72" fill="#ff8c00" stroke="#1a140f" stroke-width="2"/></svg>
      <div class="name">Slow-Moving Vehicle</div>
      <div class="meaning">Orange ▲ red border on back of farm/equipment. Max ~40 km/h.</div>
    </div>
```

### 7. School-bus-stops-at-rail factoid → existing "railway crossings" card in `#tab-rules`

Anchor: append one line inside the existing railway crossings card body.

EDIT: in `<div class="card">` containing `tag: railway crossings` + `h3: If gates drop, you stop`, add a final `<p class="pull">` line:

```html
        <p class="pull">Fun fact tested often: school buses always stop at railway crossings, train or no train.</p>
```

### 8. Tl;dr cheat-sheet — add 2 missed essentials to `#tldr` `.cheat-grid`

Anchor: in the existing "📏 Numbers to memorize" cheat block, add 2 extra `<li>` lines at the end:

```html
        <li>HOV lane: <strong>2+</strong> occupants (or green-plate EV)</li>
        <li>Lending your licence: <strong>never. illegal.</strong></li>
```

---

## Length budget check

Existing index.html: 1420 lines. Planned additions are ~80 lines of new HTML. Net growth ~5–6%, well under the 40% ceiling. Brevity preserved.

## Order of operations for Phase 4

1. Re-read index.html (post-a11y).
2. Apply edits in this order to minimize anchor drift: 8 (cheat list) → 7 (rail one-liner) → 6 (sign) → 5 (pavement section) → 4 (penalties card) → 3 (g1 card) → 2 (rules card) → 1 (behaviour card).
3. Spot-check each new card's class names + voice match.
4. Final read-through.
