# ny — Chichewa · NOTES

The Hebrew Bible rendered into Chichewa from the Hebrew, token by token, under
the rails at `docs/methodology/translation-discipline/ny.md` (selah repo).
Version 1. Not yet seated. Every pass below is its own commit in this repo.

## Burn signature

- Lit 2026-09-21 01:41 EDT on the serving lane (9 permits), engine-side relay,
  batch 4 → batch 2 → move on. 40–70 verses a minute; slowest in Job and the Psalms.
- First pass landed 09:39 EDT with 116 residue; two refill relays brought it to
  23,212 of 23,213 with residue 0. Later re-presses are named below.
- **The present-but-wrong class.** The relay fills only what is *missing*; a verse
  file that is present with an empty token array, or a row more or fewer than the
  floor, is never retried. `dev/scripts/count_mismatch_prune.py ny --apply` ran
  every half hour through the burn and handed ≈150 such files back.

## The gates

| gate | at | the Name | erasure words | bleed |
|---|---|---|---|---|
| 1 | 1,220 verses | all Yahwe | none | none real (kama · mkono · ndiyo whitelisted as Chichewa's own) |
| 2 | 4,136 | 1,071 of 1,071 | none | 0 |
| 3 | 15,174 | 5,220 of 5,222 — one *Yehova* (2 Kgs 8:10, re-pressed), one drifted surface | none | 3 verses (*na* ×2, *mtu*), re-pressed; *bwana* (a human master) and *kwenikweni* whitelisted |
| final | 23,213 — 09-21 12:10 EDT | 6,828 of 6,828 Yahwe | none | *kweni* 2 · *mbingu* 1 (Tumbuka / Swahili, three verses — hand list) |

After landing, the floor-guided scan found **no erasure word on any Name seat**.

## What the press got wrong, and what was done

1. **The rails spoke inside a verse.** Isa 53:5 came out *m'mabulaketi ake
   tachiritsidwa* — "in his brackets we are healed"; the same word at 2 Sam 14:30;
   *tokeni* once more after landing. All re-pressed. The rails' own technical words
   (mabulaketi · tokeni · themometa) are now a standing grep at every census, and
   the next chair's rails say so in plain words.
2. **The number class — the chair's deepest fault, cured in part.** Chichewa
   builds six to nine on five (*zisanu ndi chimodzi* 6 · *ndi ziwiri* 7 ·
   *ndi zitatu* 8 · *ndi zinayi* 9) and tens and hundreds on those again. The press
   got them wrong on both surfaces, and it took four passes to see how widely:
   - **6–9 in the rows:** the Sabbath came out *tsiku lachisanu ndi limodzi*, the
     sixth day (Gen 2:2–3; Exod 20:11). A number table went into the rails;
     306 verses re-pressed; misses 322 → 28 → 10.
   - **The tens:** fifty came out sixty (Gen 18:26, 28), the twentieth the twelfth
     (Hag 2:10), digits stood inside verses. Table widened to 11–19 and the tens;
     90 verses re-pressed; 88 → 11.
   - **The flows** (a row scan is blind to the flow): Genesis 5 read by eye gave
     *zaka nine … mazana nine*, 3,700 garbled (1 Chr 12:28), two hundred shields
     come out twenty (1 Kgs 10:16). A table did not cure it; **worked examples**
     did: 207 verses re-pressed, flownumber 199 → 29, and the examples' own verses
     read true.
   - **What is NOT cured.** Read by eye after the last pass: Gen 11:13 says *seven*
     years where the Hebrew says three; Num 1:21 (46,500) has lost its *thousand*.
     Neither is visible to any scan here — the scans see only six-to-nine stems,
     the tens, English words and digits. **About 2,400 verses carry a number.
     ny v1's numbers want a full audit — a judge pass over every number-bearing
     verse against the Hebrew's number, or a reader who knows the language —
     before seating.** Six seats were mended by hand from the table (80 · 70 ·
     ninth; files carry `"hand"`).
   *Any chair whose language builds numerals by addition wants the same care
   from its first gate: read a genealogy by eye.*
3. **Bless.** *-dalira* is *rely on*; *-dalitsa* is *bless*. The press wrote
   *akudalire* on bless seats. Re-pressed by seat; five that came back the same
   were mended by hand (Num 6:24 · Gen 27:10 · Gen 27:25 · Deut 23:21 · Ps 128:5 —
   each file carries `"hand"`). *-dalira* stands wherever the Hebrew means trust.
4. **Hebrew surfaces.** 418 restored from the floor (`surface_restore.py`). 80 of
   them had letters of other alphabets standing in for Hebrew ones — Cyrillic м ш
   в н for מ ש ב נ, Latin tails (*עשרim*, *עלion*), one Arabic waw — logged in
   `audit/surface-restore-2026-09-21.txt`. Verses whose rows had moved or held
   placeholders (Exod 38:19 · 2 Chr 28:2 · Ezek 48:32 · Num 32:6 · Ps 112:9) were
   re-pressed, not restored.
5. **Markers.** 79 fabricated row markers stripped (each checked against the
   floor's surface; none sat on an את-family word). 2 bare את in flows bracketed.
   434 flows brought to parity with their rows (`flow_parity.py`). 285 flow markers
   stripped in verses that hold no את at all. 98 verses whose flows still carry
   more markers than their rows: `audit/flow-gains-hand-2026-09-21.txt`.
6. **English ⟨the⟩** in 16 rows and 110 flows — stripped; Chichewa has no article.
   Swept again after every re-press.
6a. **Empty glosses.** 359 rows in 309 files had no gloss (the press folding a
   Hebrew word into its neighbour; the floor has 10 such rows). A rails line —
   every Hebrew word keeps its own gloss — and one re-press: 359 → 23.
6b. **The Name misspelt** *Yahweh* for *Yahwe* in 20 files — re-pressed, the rest
   respelt in place.
6c. **Dan 3:12** — the Aramaic object marker יתהון carries ⟨את⟩ in the rows where
   the floor carries none. Left: Aramaic is unruled across the fleet.
7. **Homoglyphs in the Chichewa itself** — ≈45 files with a Cyrillic or Greek
   letter inside a Latin word. Reported by `ny_census_fixes.py`, not yet mended.

## Cruxes

- **Exod 3:14** took the future (*Ndidzakhala amene ndidzakhala*). Whether the seat
  is a Name or the verb is Scott's fork, open across the fleet.
- ***chizindikiro*** is Chichewa's own word for a sign (אות). It convicts only
  beside a marker, where it is the rails speaking.
- ***nchi*** in flows is a malformed *n'chiyani* (מה), not Swahili *nchi*.
- **Suffixed markers** (אתכם · אתו · אתי): Chichewa carries the object inside the
  verb, so a flow can lawfully hold the sense with nowhere obvious to set the
  marker. The remaining short flows are of this kind.

## For a native ear

Lev 8:35 *ndinallamulidwa* · Exod 20:2 *m'dzikoli la* · Isa 7:14 *adzatabwala*,
*mwiniu* · Ps 23:1 *wabusanga* · Jer 31:31 *banja la* for בית · Gen 2:2 *naperamu* ·
Gen 2:3 *adaikatira ⟨את⟩ li* · Gen 5:7 *anaħyapo* (a foreign letter in a Chichewa
word) · the order of hundreds and units in Genesis 5's ages.

## The final scan (09-21, after the last pass)

`ny_census_fixes.py`: fabricated 1 (Dan 3:12) · missing 0 · bare 0 · short 0 ·
erasure 0 · convict 0 · number 20 · flownumber 29 · homoglyph 45 files.
`ny_gate`: את surfaces 9,615 — 12 without a marker in the row (the floor carries
none on them either — not read one by one; likely את as *with*), 1 fabricated (Dan 3:12).
12 flows with a non-Latin letter outside brackets.

**The hand list:** the 20 + 29 number seats the scan still names · Gen 11:13 ·
Num 1:21 · the three bleed verses · 45 homoglyph files · 98 flows with more markers
than their rows (`audit/flow-gains-hand-2026-09-21.txt`) · the native-ear list.

## Open

- **The number audit** (above) — the one thing that should hold the seating.

- The UI catalog (1,615 keys) is not yet made — it gates seating, not the text.
- Seating, ingest and the roster flip wait on Scott's word. Nothing is pushed.

## Tools (selah repo, `dev/scripts/`)

`ny_gate.clj` · `ny_census_fixes.py` (fabricated · missing · bare · short · erasure ·
convict · number · homoglyph; `--apply`, `--convict`) · `surface_restore.py ny` ·
`flow_parity.py ny` · `count_mismatch_prune.py ny`.
