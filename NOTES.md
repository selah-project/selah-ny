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
| final | see the last section | | | |

After landing, the floor-guided scan found **no erasure word on any Name seat**.

## What the press got wrong, and what was done

1. **The rails spoke inside a verse.** Isa 53:5 came out *m'mabulaketi ake
   tachiritsidwa* — "in his brackets we are healed"; the same word at 2 Sam 14:30;
   *tokeni* once more after landing. All re-pressed. The rails' own technical words
   (mabulaketi · tokeni · themometa) are now a standing grep at every census, and
   the next chair's rails say so in plain words.
2. **The number class (found 09-21 10:30 EDT).** Chichewa builds six to nine on
   five — *zisanu ndi chimodzi* 6 · *ndi ziwiri* 7 · *ndi zitatu* 8 · *ndi zinayi* 9 —
   and the press often ended them on the wrong stem. **The Sabbath came out *tsiku
   lachisanu ndi limodzi*, the sixth day** (Gen 2:2–3; Exod 20:11); Genesis 5's
   ages were mangled. ≈320 seats. A number table keyed to the Hebrew words was
   added to the rails, 306 verses re-pressed under it (misses 322 → 28), and the
   28 re-pressed once more. What still misses is on the hand list.
   *Any chair whose language builds numerals by addition wants the same scan.*
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

## Open

- The UI catalog (1,615 keys) is not yet made — it gates seating, not the text.
- Seating, ingest and the roster flip wait on Scott's word. Nothing is pushed.

## Tools (selah repo, `dev/scripts/`)

`ny_gate.clj` · `ny_census_fixes.py` (fabricated · missing · bare · short · erasure ·
convict · number · homoglyph; `--apply`, `--convict`) · `surface_restore.py ny` ·
`flow_parity.py ny` · `count_mismatch_prune.py ny`.
