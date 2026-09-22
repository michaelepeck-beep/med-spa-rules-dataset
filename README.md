# Med Spa Regulations — an open citation dataset

A free, source-linked index of what each US state's law says about operating a medical spa.
One row per state × question. Every row names the **statute or board rule** the answer was
read from, the **URL it was read at**, and the **date of that read**.

Published by [MedSpaRadar](https://medsparadar.com). The living version, with the rule text
rendered beside each citation, is at **<https://medsparadar.com/data>**.

| | |
|---|---|
| **Rows** | 1,094 |
| **States** | 51 (50 states + District of Columbia) |
| **Questions** | 27 |
| **Distinct primary-source hosts** | 99 |
| **Verification dates** | 2026-07-26 → 2026-09-20 |
| **Rows whose cited document was re-read and judged to support the sentence** | 1,094 of 1,094 |
| **Licence** | [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) |

## ⚠️ Read this before you use a row as an answer

**This dataset records which document was consulted. It does not state what the rule permits.**
There is no `answer`, `verdict`, `permitted` or `status` column, and there never will be — a
yes/no is a paraphrase of a rule, and a paraphrase is the thing that gets someone sued.

Three specific limits, each measured rather than asserted:

1. **A cited rule does not always settle the question it is filed under.** Measured on
   2026-09-22 across **1,044 of these 1,094 rows** (the 50 not measured are rows for which no
   short answer had been drafted), by a classifier run independently of the drafter:
   **281 settle the question outright; 763 bear on it without resolving it** — 27% and 73%.
   (Stability: 150 records sampled three times, 146 unanimous, 4 split.) The
   dominant cause is *sourcing depth*, not unclear law — typically we cite one board where
   the question touches several. Treat a citation as a pointer to the document, not as a
   determination.

2. **A missing state means we hold no citation, not that the answer is no.** Absence in this
   file is a statement about our reading, never about the law.

3. **`attested` means the cited document was re-read and judged to support our sentence.**
   It is a provenance check, not a legal opinion, and it says nothing about limit 1.

Not legal advice. Read the cited source, check its effective date, and confirm anything you
intend to act on with health-law counsel.

## Files

| file | description |
|---|---|
| `med-spa-rules.csv` | RFC 4180 CSV — every field quoted, embedded quotes doubled, CRLF rows |
| `med-spa-rules.json` | The same rows, plus the licence, the attribution line and the counts inline, so a stray copy can still be attributed |

## Columns

| column | type | description |
|---|---|---|
| `state` | string | USPS abbreviation, e.g. `TX` |
| `stateName` | string | Full state name |
| `question` | string | Question slug, e.g. `can-a-non-physician-own-a-med-spa` |
| `questionLabel` | string | Short human label for the question |
| `citation` | string | The rule as cited — statute or administrative code section |
| `sourceUrl` | string | The citation of record, on the publisher's own site |
| `readAt` | string \| "" | Where the text was actually READ, when that differs from `sourceUrl` — see below |
| `readAtName` | string \| "" | Human name of that host |
| `verified` | date | The date the cited document was last read |
| `attested` | boolean | The cited document was re-read and judged to support the sentence |
| `page` | url | The page on medsparadar.com showing the rule text for this row |

### `readAt` — why the citation and the reading can differ

99 of 1,094 rows carry a `readAt`. Some states do not publish their own code in a form any
automated client can read; a few designate a commercial publisher as the public copy and say
so themselves. Where that happens the **citation of record stays on the official publisher**
and only the *reading* moves, with the host named here rather than quietly substituted. A row
where `readAt` is empty was read at `sourceUrl`.

## The 27 questions

Ownership and corporate practice · business structure · management companies · private equity
· medical director · supervising physician duties · cosmetic lasers · medical assistants ·
pre-treatment exam (required / by telehealth / by whom) · on-site presence · RN injection ·
nurse practitioner independence · physician assistant scope · med spa registration ·
responsible practitioner · board reporting · advertising · deceptive-marketing enforcement ·
unlicensed practice · shutdown authority · discipline grounds · compounded GLP-1 ·
non-clinical revenue share · esthetician microneedling · cost to open.

## Attribution

> Med spa regulatory citations by MedSpaRadar (medsparadar.com), CC BY 4.0

## Provenance

Regenerated from the same resolver that renders the public pages, so a row's citation, date
and URL equal what its `page` publishes. Legislative data via LegiScan (CC BY 4.0).
