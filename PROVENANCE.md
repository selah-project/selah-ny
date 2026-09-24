# PROVENANCE — how this rendering came to be

*Chichewa (Chinyanja), chair 89. Lit 2026-09-21. Floor 23,213 verses.*

This is the record of how the text in this repository was produced and
what went wrong with it. A machine-assisted rendering has no standing
unless you can see how it was made, so this file says both. The
pass-by-pass working notes are in [NOTES.md](NOTES.md).

---

## The approach

Every verse is rendered from the Hebrew of that verse, under a written
discipline — `docs/methodology/translation-discipline/ny.md` in the
Selah repository, itself written in Chichewa and following the shape of
the Bantu sister chair `xh.md` (isiXhosa). The rules that govern it:
the Hebrew token is the unit; the Name stays the Name; both truths of
Deuteronomy 6:4; no foreknowledge (Genesis 22:1 does not know Genesis
22:13); numbers and letters stay put; the translator has no word of its
own; hard places go in bare.

**The `⟨ ⟩` brackets do two different jobs.** `⟨את⟩` is the Hebrew
direct-object marker, which Chichewa has no word for; it is left
standing so the reader sees it. `⟨liwu⟩` is a word the Hebrew did not
write but Chichewa grammar requires — visibly marked, so you can always
tell what the Hebrew said from what the grammar needed.

Every verse file carries the model that wrote it: **glm-5.3**, on the
**glm-5.2** tier.

## The Name

| Hebrew | here | rejected |
|---|---|---|
| יהוה | **Yahwe** | Yehova, Chauta, Ambuye, Mulungu in the Name's place, Mphambe, Namalenga |
| אלהים | **Elohim** | Mulungu in the Name's place |
| אדני | **Adonayi** | Ambuye |
| שדי | **Shadayi** | Wamphamvuyonse as the whole rendering |
| אל | **El** | *mulungu* as a type-name |
| צבאות | **Tsevaoti** | "wa makamu" |

Lowercase *mulungu* / *milungu* over the nations' gods and *mbuye* over
a human lord remain lawful; the census applies that distinction by the
token's Hebrew surface, never by the Chichewa spelling.

**Name seats reading Yahwe: 6,828 of 6,828.** No erasure word stands on
any Name seat.

## The burn and the gates

Lit 01:41 EDT on the serving lane (9 permits), engine-side relay, batch
4 → batch 2 → move on; 40–70 verses a minute, slowest in Job and the
Psalms. The first pass landed 09:39 EDT with a residue of 116; two
refill relays brought the floor whole.

Four gates were read by hand — at 1,220 · 4,136 · 15,174 verses and at
the end (12:10 EDT). The third gate found one *Yehova* (2 Kings 8:10)
and three verses of neighbour-language bleed; all were re-pressed.

The corpus was committed to git **before any pass touched it**
(`8089bea3`, "the burn as it landed"), so every repair below is a diff
you can read.

## Finding: the relay never retries a verse that is present but wrong

The relay fills only what is *missing*. A verse file that is present
with an empty token array, or with a row more or fewer than the floor,
is never retried. `dev/scripts/count_mismatch_prune.py ny --apply` ran
every half hour through the burn and handed roughly 150 such files
back.

## Finding: the numbers — this chair's deepest fault

Chichewa builds six to nine on five (*zisanu ndi chimodzi* 6 · *ndi
ziwiri* 7 · *ndi zitatu* 8 · *ndi zinayi* 9), and the tens and hundreds
on those again. The press got them wrong on both surfaces, and it took
four passes to see how widely:

| pass | what was wrong | misses |
|---|---|---|
| rows 6–9 | the Sabbath came out the sixth day (Gen 2:2–3; Exod 20:11) | 322 → 28 → 10 |
| the tens | fifty came out sixty (Gen 18:26, 28); the twentieth the twelfth (Hag 2:10) | 88 → 11 |
| the flows | a row scan is blind to the flow: Genesis 5's ages, 3,700 garbled (1 Chr 12:28), two hundred shields come out twenty (1 Kgs 10:16) | 199 → 29 |
| worked examples | a table did not cure the flows; **worked examples in the rails did** | the examples' own verses read true |

**What is not cured.** Read by eye after the last pass: Genesis 11:13
says *seven* years where the Hebrew says three; Numbers 1:21 (46,500)
has lost its *thousand*. Neither is visible to any scan here — the
scans see six-to-nine stems, the tens, English words and digits, and
nothing else. About 2,400 verses carry a number. **ny wants a full
number audit — a judge pass over every number-bearing verse against the
Hebrew's number, or a reader who knows the language — and that is the
one thing that should hold its seating.**

*Any chair whose language builds numerals by addition wants the same
care from its first gate: read a genealogy by eye.*

## Finding: the rails can speak inside a verse

Isaiah 53:5 came out *m'mabulaketi ake tachiritsidwa* — "in his
brackets we are healed" — the document's own word for a bracket
standing where חבורתו belongs. The same word turned up at 2 Samuel
14:30, and *tokeni* once more after landing. All were re-pressed, and
the rails' technical words (*mabulaketi* · *tokeni* · *themometa*) are
now a standing grep at every census.

## Finding: two verbs one letter apart

*-dalira* is *rely on*; *-dalitsa* is *bless*. The press wrote
*akudalire* on bless seats. Those were re-pressed by seat, and five
that came back the same were mended by hand. *-dalira* stands wherever
the Hebrew means trust.

## Finding: the chair spends its own alphabet into the Hebrew

418 Hebrew surfaces were restored from the floor
(`dev/scripts/surface_restore.py ny`). 80 of them had letters of other
alphabets standing in for Hebrew ones — Cyrillic м ш в н for מ ש ב נ,
Latin tails (*עשרim*, *עלion*), one Arabic waw — all logged in
`audit/surface-restore-2026-09-21.txt`. Five verses whose rows had
moved or held placeholders (Exod 38:19 · 2 Chr 28:2 · Ezek 48:32 ·
Num 32:6 · Ps 112:9) were re-pressed rather than restored: the Hebrew
is never the chair's to write.

## The cure, in order

| pass | what |
|---|---|
| refill relays ×2 | the 116 residue seats |
| surface restore | 418 surfaces, 80 of them cross-alphabet |
| markers | 79 fabricated row markers stripped · 2 bare את bracketed · 434 flows brought to parity · 285 flow markers stripped in verses holding no את at all |
| English ⟨the⟩ | 16 rows and 110 flows — Chichewa has no article to supply |
| re-press 1 | 129 verses — *bless*, neighbour words, one rails word, short flows |
| re-press 2 | 306 verses — the 6–9 number class, under a number table added to the rails |
| re-press 3 | 90 verses — the tens, and the Name misspelt *Yahweh* in 20 files |
| re-press 4 | 309 files — rows with an empty gloss (359 → 23) |
| re-press 5 | 207 verses — the flow numbers, under worked examples |
| hand seats | nine files carry a `hand` field: five bless seats (Num 6:24 · Gen 27:10 · Gen 27:25 · Deut 23:21 · Ps 128:5) and four number seats (Exod 7:7 · Exod 38:28 · Exod 38:29 · 2 Chr 17:18), each naming its fault and the rails' row that cured it |

## Open — declared, not repaired

- **The number audit** — above. The one item that should hold the
  seating.
- **Genesis 11:13** (*seven* for three) and **Numbers 1:21** (a lost
  *thousand*) — found by eye, not by scan.
- **Homoglyphs in the Chichewa itself** — roughly 45 files with a
  Cyrillic or Greek letter inside a Latin word. Reported, not mended.
- **The ⟨את⟩ gap** — 98 flows carry more markers than their rows
  (`audit/flow-gains-hand-2026-09-21.txt`), and Chichewa carries the
  object inside the verb, so a flow can hold the sense with nowhere
  obvious to set the marker. Left for a reader, not guessed.
- **Daniel 3:12** — the Aramaic object marker יתהון carries ⟨את⟩ where
  the floor carries none. Aramaic is unruled across the fleet.
- **אדון at a divine seat** (Isa 1:24 · Josh 3:11 and their like) has no
  row of its own in the Name table; the chair wrote *Adonayi* there.
- **Words for a native ear** — the coined method terms (*khesedi*,
  *Sheoli*, *Mashiya*, *Tsevaoti*, *pangano*), *adalenga* against
  *analenga*, and the list at the end of NOTES.md.
- **Counted at writing (2026-09-24):** 23 rows still hold an empty
  gloss; 77 flows use ASCII `<…>` where the angle brackets ⟨…⟩ belong;
  37 words in the Chichewa carry a letter of another alphabet. Every
  Hebrew surface matches the floor's consonants.

## Final

**23,213 / 23,213 verses.** Yahwe in **6,828 of 6,828** Name seats, no
erasure word on any of them. Every Hebrew surface bare consonants, as
given. The numbers wait on an audit.
