+++
title = "+विषय-वाक्य-दीपिका"

+++

अथ विषयवाक्यदीपिका
(श्रीरङ्गरामानुजमुनिप्रणीता)

अतसी-गुच्छ-सच्छायम्  
अञ्चितोरस्स्थलं श्रिया ।  
अञ्जनाचल-शृङ्गारम्  
अञ्जलिर् मम गाहताम् ॥ १ ॥

व्यासं लक्ष्मण-योगीन्द्रं  
प्रणम्यान्यान् गुरून् अपि ।  
भाष्योदाहृत-वेदान्त-  
वाक्यार्थस् सम्प्रकाश्यते ॥ २ ॥

विस्तृतोपनिषद्-भाष्य-  
प्रवेशाक्षम-चेतसाम् ।  
अनुग्रहेण साफल्यं  
कृतिर् एषा प्रपत्स्यते ॥ ३ ॥

<details><summary>AI prompt</summary>

**AI prompt — interleaving this dīpikā into a bhāṣya page**

**Goal.** Given one adhikaraṇa of this dīpikā (e.g. `1/1/09_jyotiradhikaraNam.md`,
`1/1/10_indraprANAdhikaraNam.md`) and the upaniṣad page carrying the प्रकाशिका it comments on (e.g.
`vedAH_sAma/.../rangarAmAnujaH/3/12_brahma-gAyatry-upAsanam.md`,
`vedAH_Rk/.../rAmAnujIyam/sarva-prastutiH/03.md`), interleave the दीपिका into that page,
**splitting every existing block at the boundaries the dīpikā itself uses**, so that each group of
प्रस्तुति / मूलम् / दीपिका / प्रकाशिका treats the same unit of text. The dīpikā supplies प्रस्तुति +
दीपिका; the page's own मूलम् and प्रकाशिका are only re-cut, never rewritten.

**1. Block vocabulary and order**

Within one **group** (one dīpikā-quoted core-text unit), the order is fixed:

1. `<details open><summary>विश्वास-प्रस्तुतिः</summary>` — **always `open`**, every group.
2. `<details><summary>मूलम्</summary>`
3. `<details><summary>रङ्गरामानुजः - विषय-वाक्य-दीपिका</summary>`
4. `<details><summary>रङ्गरामानुजः - प्रकाशिका</summary>`

Blank line between blocks; body is `\n\n<text>\n</details>`.

**2. The source is the segmentation authority**

- Every **quoted passage** in the dīpikā (`> "…"` block) opens a new group. Nothing else does; do not
  invent boundaries from the sense.
- Dīpikā prose **before** the section's first quote (intro, ending in `…इति प्रतिपादयति —`,
  `…इत्यत्राह —`, `…आह —`) becomes a **pre-block**: दीपिका-only, closed, placed before the first
  प्रस्तुति, directly under the `##` heading (or under the `###` label hoisted from the pre-block's
  first line, if it has one).
- Dīpikā prose **after** the last quote belongs to the last group's दीपिका (colophons stay plain
  paragraphs at the end).

**3. Per-block derivation**

| block | comes from | rule |
|---|---|---|
| प्रस्तुति | the dīpikā quote | copy the dīpikā's presentation of the core text verbatim, strip `>` and surrounding `"…"`, keep embedded `+++(…)+++` notes |
| मूलम् | page's existing mūla | split at the same substrings |
| दीपिका | dīpikā prose between this quote and the next | slice source line ranges; keep line breaks and double trailing spaces |
| प्रकाशिका | page's existing prakāśika | re-cut at the same boundary, usually at the sentence quoting the same core text (often after `**प्र.–**`) |

**4. Splitting technique (no retyping, ever)**

- Use a build script: slice the dīpikā by **line ranges**, split page blocks with
  `split_seq(text, markers)` where each marker is asserted `text.count(marker) == 1`.
- If a split point is invisible because of sandhi, restore the sandhi **only in the मूलम् being
  split**, never globally.
- The script must read **dīpikā + a saved copy of the pre-change page**; once installed the page is
  already re-cut and the script is not re-runnable.
- The vishvAsa trees are **not git repos**: copy the page to a backup before overwriting.

**5. Punctuation, headings, breaks**

- **Hoisted headings.** A dīpikā `##`/`###`/`####` heading that is the **first line of a दीपिका
  block** (including the first line of a pre-block) is separable from the prose: render it as a real
  `### name` heading immediately **before the प्रस्तुति block it labels** — one blank line before the
  heading, **no blank line** between the heading and `<details open>`, e.g.

  ```
  ### चराचरग्रहणात्
  <details open><summary>विश्वास-प्रस्तुतिः</summary>
  ```
- **Mid-block headings stay bold.** A heading that appears **inside** a दीपिका block, after its prose
  has already begun, cannot be moved without breaking the commentary sequence: keep it bold inside the
  block — `**name॥**` plus two trailing spaces (hard break), e.g. `**औचित्यम्॥**  `.
- A dīpikā heading already mirrored by the page's own `##` heading is **dropped**. If the label is
  still informative it may be hoisted as `###`, so a page `##` and a `###` may sit adjacently.
- A page with no `##` headings of its own (e.g. `.../sarva-prastutiH/03.md`) gets `###` headings in the
  running text, at the same positions.
- **Never rstrip** dīpikā prose lines: they carry meaningful trailing double spaces (hard breaks),
  one clause per line.
- Lead-in sentences stay at the **end of the preceding** दीपिका block. Exception: section labels
  (`**फलम्॥**`, `**दृष्टिः॥**`, `**श्रुतिः॥**`, `**फलादि॥**`, `**महिमा॥**`, `**उपासनम्॥**`) do not
  open a bold line inside the block — they are **hoisted to `###`** before the प्रस्तुति they label.
- **No दीपिका block may start or end with a bold heading.** A leading label is hoisted to `###` before
  the block's प्रस्तुति; a label standing immediately before a quote with no prose of its own
  (`**वर-प्रार्थना॥**`) is likewise hoisted to `###` before the first group's प्रस्तुति.
- Verse numbers `॥ n ॥` from the dīpikā's quote stay **inside मूलम् where they fall**; a quote
  straddling two verses may thus put two verse markers mid-block. Fidelity beats alignment.
- खण्ड-/adhyāya-end markers get a प्रस्तुति+मूलम् pair; colophons and footnotes stay plain at EOF.

**6. Verification checklist**

1. **Coverage**: every line of the dīpikā's section range appears verbatim in the page after
   stripping `>`, surrounding quotes and heading markers → expect `missing: []`.
2. `<details>` count == `</details>` count.
3. Summary census matches intent; all प्रस्तुति blocks `open`.
4. Sections not being edited are byte-identical before/after.
5. No stray `None` (generator sentinel).
6. Structural lint: no दीपिका/प्रकाशिका block starts or ends with a `**…॥**` heading — a leading label
   is a `###` heading before the प्रस्तुति, and only mid-block labels stay bold; block order is always
   प्रस्तुति → मूलम् → दीपिका → प्रकाशिका; no empty blocks; exactly one `**n**` verse marker per
   मूलम् verse; the page's verse markers are all still present, each once.

Applied so far: ChAndogya 3/12 (19/19/21/18), 3/13 (14/14/6/12); Kauṣītaki
`.../sarva-prastutiH/03.md` from `10_indraprANAdhikaraNam.md` (101/101/42/63, verses 1–67).
Heading hoisting (`###` before प्रस्तुति, bold only mid-block) applied to all three pages.

**7. Worked example of a group boundary**

Dīpikā (jyotir, first group) — quote at lines 261–263, prose 265–279:

- no pre-block
- प्रस्तुति: `अथ यद् अतः परो दिवो ज्योतिर् दीप्यते / +++(व्यष्टि-भूतेषु)+++ …`
- मूलम्: first piece of the section mūla, re-cut at `इदं वाव तद्` and `तस्यैषा दृष्टिः`
- दीपिका: `एवं गायत्री-विद्या-प्रकृतस्य … इत्याह —` through line 279
- प्रकाशिका: first piece of the section praks, re-cut at `**इदं वाव तद्`

**8. Source-to-page mapping**

The dīpikā's adhikaraṇa corresponds to the upaniṣad passage it quotes, not to the page number by
name — check the quoted sūtra/mantra before choosing the target page (e.g. `10_indraprANAdhikaraNam`
quotes the Pratardana/Indra passage = `kauShItaki .../sarva-prastutiH/03.md`, while `04.md` is the
Bālāki–Ajātaśatru passage).

</details>
