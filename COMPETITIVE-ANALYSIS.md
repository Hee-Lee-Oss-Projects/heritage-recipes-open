# Competitive & Improvement Analysis — heritage-recipes-open

> Scope: rigorous correctness review of PLAN.md (v0.1.0, 2026-06-28) + web-grounded competitive
> landscape for an **open, community-consented, attributed heritage-recipe archive**. Researched and
> cited June 2026. Lane: donated. Risk tier: low (with escalated safety/translation bands).

---

## 1. Correctness & completeness review of PLAN.md

The plan is unusually strong: it correctly treats **consent, cultural attribution, and provenance — not
volume — as the project's identity**, and it operationalizes each as a hard, countable CI gate
identical to the provenance model. It adopts the right external frameworks (CARE for Indigenous Data
Governance; TK Labels via Local Contexts; schema.org/Recipe + Cooklang/ORF interop). Below are the
correctness findings, ordered by importance.

**A. Cultural ownership / consent / benefit (the headline dimension) — mostly right, with gaps.**
- **Strong:** FPIC for community-level knowledge, restricted/sacred status (recorded-never-published),
  right-to-withdraw as a first-class propagating operation, TK Labels, and CARE adoption. This is the
  correct posture and matches the state of the art — CARE explicitly exists *because* FAIR/"open"
  ignores power differentials and historical context (gida-global.org). The plan even names the
  upstream-ethics point: communities must have authority **from the start**, not just at last-mile.
- **GAP — "who profits / benefit-sharing" is under-specified.** The plan covers *consent* and
  *attribution* thoroughly but barely addresses **Collective Benefit** (the "C" in CARE) as a flow of
  value *back* to communities. CC-BY-4.0 by default permits unrestricted **commercial** reuse by third
  parties (e.g. an AI company or a cookbook publisher) with attribution only — communities get credit
  but no benefit and no veto over commercial extraction. This is exactly the appropriation risk the
  plan claims to guard against, re-entering through the license. The plan should (a) make
  **benefit-sharing / non-commercial or BC (Biocultural) Label options** an explicit, contributor- and
  community-selectable choice, and (b) state a position on AI-training reuse (see G below).
- **GAP — TK Labels are non-legal notices, not enforceable licenses.** The plan treats TK Labels as a
  "cultural overlay on any license," which is correct, but should state plainly that **a TK Label does
  not restrict a CC-BY licensee** — so a community wanting genuine control needs license choice (CC-BY-NC,
  restricted status, or BC Labels), not a TK Label *over* CC-BY. Conflating the two would mislead
  communities about the protection they actually have.
- **GAP — reviewer compensation vs. extraction.** The plan flags "extractive volunteer burden" in Open
  Questions but its mitigation (sampling, rotation, SLA) addresses *burnout*, not *equity*. Asking
  origin-community members to do unpaid cultural-fidelity review **is itself an extraction vector**. The
  benefit-sharing gap (above) and this are the same problem.

**B. Attribution to elders/communities — correct and well-modeled.** The `attribution` block (named
person *with consent* / family / community / "anonymous by request") and the variant policy (co-equal,
no "authenticity winner") are right. One refinement: attribution should support **collective +
individual simultaneously** (e.g. "Recipe of Maria X, of the Y community") and capture **post-mortem
attribution** rules (an elder passes; who consents to keep their named recipe? estate? community?).

**C. Recipes-not-copyrightable-but-stories-are nuance — correct and conservative.** The plan correctly
states the U.S. doctrine: a bare ingredient list + functional procedure are facts/process (uncopyright-
able), while headnotes/prose/photos/creative compilation selection are protected. This is exactly
*Publications Int'l v. Meredith* (7th Cir. 1996) — bare recipes lacking "expressive elaboration" are
unprotected; substantial literary expression is (copyrightalliance.org). The plan's conservative choice
to **not even import facts** from in-copyright sources (citing jurisdiction variance, compilation
copyright, and ToS) is defensible and reduces legal surface. **Minor correctness note:** the plan says
"U.S. generally pre-1929" for PD — correct for 2026 (works published 1929 and earlier are PD), but the
date advances yearly; the spec should compute this, not hardcode it. Also good: it flags the
**PD-text-wrapped-in-copyrighted-scan/translation** trap and **independent photo licensing** (the most
common real-world failure).

**D. Provenance & accuracy of cultural claims — strong, with one addition.** Resolvable provenance is a
hard gate; "gaps stay gaps; AI never invents cultural attributions/history" is exactly right (see §5).
**ADD:** an explicit guard against **fabricated or romanticized "origin stories."** Cultural-history
claims ("this dish dates to the 14th-century court of…") are a high-risk fabrication zone and should be
treated like medical claims: sourced or marked as contributor-stated belief, never asserted as fact.

**E. Structured format (schema.org/Recipe) — correct base choice.** schema.org/Recipe maximizes
downstream reuse (search engines, Wikidata, recipe tools), and Cooklang/ORF interop is the right
ecosystem bet (Cooklang is an open spec with a real tool ecosystem — cooklang.org). **Caveat to
document:** schema.org/Recipe has **no native fields** for consent, FPIC, TK Labels, or cultural
attribution — these are *all* in the heritage extension, so the "schema.org compatibility" benefit
applies only to the culinary core, not the governance metadata. State this so downstream consumers
don't silently drop the consent/attribution layer on round-trip. Cooklang/ORF round-trips are
**lossy** for exactly these fields — the plan notes "lossy fields noted," which must include the entire
governance block.

**F. Open-license-WITH-consent tension — acknowledged but the irrevocability conflict is sharp.** The
plan honestly discloses that **CC licenses are irrevocable for already-distributed copies**, so
"right-to-withdraw" can only remove from project surfaces + emit a tombstone/propagation notice — it
**cannot** recall downstream copies. This is correct and honestly disclosed. But it sits in genuine
tension with CARE's "Authority to control" (ongoing, not one-time) and with the promise to
communities. **Recommendation:** consider a **default of a more revocable posture for community
knowledge** (e.g. publish under restricted/contextual access or a custom community license, with CC-BY
as an *opt-in upgrade*) rather than CC-BY-by-default with irrevocability as a disclosed footnote. At
minimum, the consent UI must make irrevocability impossible to miss.

**G. MISSING — explicit AI-training-reuse stance.** Given the project is built *by* an AI-agent
platform and produces clean structured cultural data, the single most likely "extraction" vector in
2026 is **bulk ingestion into commercial AI training sets**. The plan never addresses whether
communities can opt out of AI-training reuse. This belongs in the consent record and license menu, and
is arguably the most important missing decision.

**H. Minor/structural.** (1) `verifiedNeed: false` until a steward is secured is honest and correct.
(2) The fidelity-audit sampling frame (≥50/release, stratified by community & method, independent
auditor, back-to-source, safety/translation at 100%) is rigorous — a model other Hee-Lee Oss projects should
copy. (3) Allergen-as-hard-gate (incl. explicit "unknown") is a thoughtful safety control. (4) Consider
adding a **dietary/religious-restriction** metadata axis (halal/kosher/vegetarian/fasting traditions) —
high reuse value and culturally salient, currently absent.

---

## 2. Competitive landscape (researched, cited)

No existing project occupies the **open + structured + consent-first + culturally-attributed** quadrant.
Competitors each hold one or two axes and miss the others.

**Wikibooks Cookbook** — several-thousand user-contributed recipes across cuisines; dual-licensed
**CC-BY-SA-4.0 + GFDL**.
*Strengths:* genuinely open, large, established, Wikimedia-backed, freely reusable/derivable.
*Weaknesses:* **CC-BY-SA copyleft** forces share-alike on derivatives (interoperability friction with
CC-BY/CC0 corpora); unstructured prose (not machine-readable as data); **no consent or cultural-
attribution layer** at all; no provenance to a tradition-bearer; no FPIC/TK concept. Source:
en.wikibooks.org/wiki/Cookbook:Table_of_Contents; license per enterprise.wikimedia.org.

**schema.org/Recipe** — the dominant machine-readable recipe vocabulary (JSON-LD), used across the web.
*Strengths:* universal, well-supported, the right interop base.
*Weaknesses:* a **vocabulary, not a corpus or a governance model**; zero fields for consent, cultural
ownership, or attribution-to-community. Source: schema.org/Recipe.

**Internet Archive — Cookbook & Home Economics Collection** — ~13,000 digitized vintage/historical
cookbooks (UCLA, UC Berkeley, Prelinger), many public-domain, oldest from 1475.
*Strengths:* huge PD corpus; free download; a primary *source* the project can ethically ingest.
*Weaknesses:* **page scans, not structured data**; no per-recipe rights/structuring; skews
Western/Anglo-American; **no living-community consent** (and PD status doesn't equal cultural
permission). Source: archive.org/details/cbk; openculture.com (2022).

**University foodways archives** (UNC Southern Foodways Alliance + Southern Oral History Program; MSU
*Feeding America*; NYU Marion Nestle Collection; UW-Madison; Michigan/HathiTrust community cookbooks).
*Strengths:* deep oral-history + provenance rigor; scholarly credibility; real community engagement
(esp. SFA). *Feeding America* has 76 fully transcribed/searchable historical cookbooks.
*Weaknesses:* **siloed, institution-specific, not openly-licensed-by-default, not a shared machine-
readable schema**; regional scope (heavily U.S. South); access often gated. Sources:
guides.lib.unc.edu/southern-foodways; lib.msu.edu (Feeding America); guides.nyu.edu/foodstudies.

**SAVEUR / Whetstone / diaspora-foodways media** — Whetstone Magazine + "Point of Origin" podcast
document global and diaspora foodways (e.g. Venezuelan criolla, Indigenous decolonized diet).
*Strengths:* outstanding cultural storytelling, diaspora reach, ethical sensibility, trust with
communities. *Weaknesses:* **editorial/narrative, not structured open data**; copyrighted; not a
reusable corpus. A potential *partner/amplifier*, not a competitor. Source:
whetstonemagazine.com/journal/venezuelan-cuisine-finds-rebirth-in-diaspora.

**Indigenous food-sovereignty projects** — NĀTIFS / Indigenous Food Lab (Sean Sherman, Oglala Lakota);
I-Collective; Native Memory Project; USDA Indigenous Food Sovereignty Initiative.
*Strengths:* community-led, food-sovereignty framing, authentic authority, exactly the CARE posture.
*Weaknesses:* **mission is revitalization/economic, not building an open dataset**; recipes are assets
*controlled by* communities (often deliberately not openly published). Critical insight: these are the
**model partners and the rightful authorities** — and a reminder that "open" is sometimes the wrong
answer (restricted status matters). Sources: natifs.org; seansherman.com; usda.gov.

**Family-recipe apps** — Heirloom, Heirloom Recipe Box, Family Cookbook Project, Recipe Keeper,
Honeydew, Recipe Notes.
*Strengths:* slick UX; **direct competitors on the AI angle** — Heirloom Recipe Box does **on-device AI
structuring of spoken/handwritten recipes** and markets "73% of family recipes are lost within one
generation"; Family Cookbook Project has an AI photo-to-text "Smart Recipe Converter."
*Weaknesses:* **proprietary, closed silos, subscription paywalls, private to a family**; no open
license, no cultural-attribution/consent governance, no provenance, no interop — the opposite of an open
commons. Sources: heirloomrecipebox.app; familycookbookproject.com; apps.apple.com (Heirloom).

**Local Contexts (TK / BC Labels & Notices)** — infrastructure for Indigenous cultural authority over
data via provenance metadata, protocols, and permissions.
*Strengths:* the definitive standard for the project's attribution overlay; Labels are
community-generated (vs. institution-generated Notices). *Weaknesses:* **a labeling/governance layer,
not a recipe corpus** — complementary, a dependency, not a competitor. Sources:
localcontexts.org/labels/traditional-knowledge-labels; gida-global.org/careprinciples (CARE).

---

## 3. Gaps we can fill

1. **The empty quadrant: open + structured + consent-first + attributed.** Wikibooks is open but
   unstructured/unconsented; apps are structured but closed; archives are sourced but siloed/unlicensed;
   sovereignty projects are consented but deliberately not-open. No one ties all four together.
2. **A machine-readable consent/provenance layer for recipes.** No recipe schema in the wild carries
   FPIC, TK Labels, withdrawal semantics, and tradition-bearer attribution as countable, CI-enforced
   fields. This is genuinely novel infrastructure.
3. **Diaspora/endangered-foodways priority.** Apps target affluent nuclear families; archives skew
   U.S.-South/Anglo; this project can prioritize **at-risk and diaspora communities** explicitly.
4. **Structuring the PD backlog ethically.** 13,000 IA cookbooks are scans; turning *verified-PD,
   facts-only* recipes into clean structured data (with provenance, no protected photos) is unfilled.
5. **An interop bridge** between schema.org/Recipe, Cooklang, ORF, and Wikidata with cultural metadata
   preserved — nobody round-trips the *governance* layer today.
6. **Withdrawal/propagation tooling** for a distributed open corpus — essentially nonexistent in the
   open-data world and a real CARE-aligned contribution.

---

## 4. Differentiators to win

- **Consent & cultural ownership as first-class, CI-enforced data** — not a policy PDF but a build-
  breaking gate. Nobody else does this for recipes.
- **CARE + FAIR together** (not FAIR alone) with TK/BC Labels and restricted status — credibility with
  exactly the communities everyone else extracts from.
- **Right-to-withdraw that actually propagates** — a working ethical control, demonstrated end-to-end.
- **Open AND governed** — the family-app polish (AI structuring) but as an *open commons* with
  community authority, not a paywalled silo.
- **Honest scoping** (`verifiedNeed:false`, maintained-but-not-shipped) — builds trust that the project
  serves communities, not metrics.
- **Diaspora/endangered-first** prioritization — a values-aligned wedge the incumbents ignore.

---

## 5. Claude API leverage — and the hard limits

**Where Claude adds leverage (always assistive, human/community-confirmed):**
1. **Transcription & structuring** — turn a tradition-bearer's spoken account, handwritten card, or
   PD-cookbook OCR into a typed schema.org/Recipe record (ingredients, quantities metric+customary,
   ordered steps), **flagging — never guessing — ambiguous quantities, unfamiliar ingredients, unclear
   technique.** Directly counters the closed on-device-AI apps (Heirloom Recipe Box) with an *open*
   equivalent.
2. **Metadata & normalization** — propose allergen tags, safety-critical-band detection
   (canning/fermentation/curing/raw/foraging/infant → route to human review), unit normalization, and
   schema/Cooklang/ORF round-trip mappings; draft data-dictionary and reuse docs.
3. **Translation drafting (then fluent-reviewer fidelity check)** — original language always retained;
   Claude drafts, a fluent community reviewer ratifies (100% reviewed per plan).
4. **Reconciliation assist** — suggest Wikidata ingredient/place links for human confirmation; detect
   missing-field/anomaly flags for QA.
5. **Consent/licensing intake assist** — help structure (not decide) consent records and flag sources
   that look proprietary/in-copyright for the licensing reviewer.

**Where Claude must NOT decide (governance-reserved):**
- **Cultural ownership, consent, and FPIC** — who may consent on a community's behalf is a community
  governance question (CARE Authority-to-Control); Claude can record, never grant.
- **Attribution** — how/whether an elder or community is named is the contributor's/community's choice,
  not a model inference.
- **Cultural context/history** — **no fabricated or romanticized origin stories, dates, or "authenticity"
  claims.** Unsourced history is marked contributor-belief or omitted. Gaps stay gaps.
- **Accuracy of the recipe itself** — verified by the tradition-bearer (back-to-source), not the model.
- **License selection & restricted status** — a human/community decision, especially the irrevocability
  trade-off and any AI-training-reuse opt-out.
- **Food-safety adequacy** — model flags the band; a competent human signs off against USDA/NCHFP.

---

## 6. Ten concrete optimizations

1. **Add a Collective-Benefit / benefit-sharing decision** to the consent record and license menu
   (incl. **CC-BY-NC and BC Labels** as first-class options), closing the CARE-"C" gap where CC-BY-by-
   default re-opens commercial extraction.
2. **Add an explicit AI-training-reuse opt-out field** to the consent record (the dominant 2026
   extraction vector for clean structured cultural data).
3. **State plainly that a TK Label does not bind a CC-BY licensee** — pair real control with license
   choice/restricted status, not a TK overlay alone, so communities aren't misled about protection.
4. **Reconsider the default license posture for *community* knowledge** — restricted/contextual or a
   custom community license as default, with CC-BY as an opt-in *upgrade*, given CC irrevocability vs.
   CARE Authority-to-Control.
5. **Budget reviewer compensation** for cultural-fidelity reviewers from origin communities (not just
   rotation/SLA) — unpaid community review is itself extraction.
6. **Treat cultural-history/origin claims like medical claims** — sourced or marked
   contributor-stated-belief; a fabrication guard alongside the existing health-claim guard.
7. **Compute PD cutoffs, don't hardcode** ("pre-1929"); add per-edition scan/translation/photo rights
   sub-checks as a checklist in the eligibility gate.
8. **Document that schema.org/Recipe + Cooklang/ORF round-trips drop the governance block** (consent/
   FPIC/TK/attribution are lossy) and require the JSON-LD canonical form to travel with any export.
9. **Add dietary/religious-restriction metadata** (halal/kosher/vegetarian/fasting/ceremonial) — high
   reuse value, culturally salient, currently missing.
10. **Add collective + post-mortem attribution rules** (collective+individual simultaneously; who
    consents to keep a deceased elder's named recipe) to the attribution/consent spec.

---

## 7. Parallel & perpendicular spin-offs

**Parallel (same engine, sibling corpora):**
- **world-folktales-open** — folktales share the *exact* governance problem (oral, community-owned,
  appropriation-prone, story-is-copyrightable-but-motif-isn't). Reuse the consent/FPIC/TK/withdrawal
  schema almost verbatim.
- **public-domain-translations** — the fluent-reviewer fidelity-check pipeline and translator-credit
  model transfer directly to translating recipes *and* folktales.
- **local-history-stubs** — community provenance + oral-history capture + persistent-ID scheme are
  shared; a local-history record can *reference* a heritage recipe (a dish tied to a place/event).
- **multilingual-museum-labels** — heritage recipes ARE museum objects; the TK-Label-in-JSON-LD work
  and original+translation display are common infrastructure.

**Perpendicular (new surfaces from the same data):**
- **community-foodways archive** — a richer sibling adding oral-history audio, foodways context, and
  ingredient/foraging knowledge (with stronger restricted-knowledge handling) — a natural home for the
  NĀTIFS/SFA-style partners.
- **A heritage-recipe MCP server** — expose the consented, attributed corpus over MCP so *any* agent can
  query recipes **with attribution, consent status, allergens, and TK Labels surfaced** — turning the
  governance metadata into a feature rather than something downstream tools silently strip. (Read-only;
  restricted recipes never exposed; withdrawal propagates.)
- **A reusable "consent-first open-data" toolkit** — the CI consent/attribution/provenance/withdrawal
  gates extracted as a generic package other CARE-aligned open-data projects adopt.

---

## 8. Open questions

- **Benefit-sharing & commercial reuse:** does CC-BY-by-default betray the anti-extraction mission? Is
  CC-BY-NC / BC Labels / restricted-by-default the more honest stance for community knowledge?
- **AI-training reuse:** can communities opt out, and how is that expressed in a machine-readable,
  enforceable-as-possible way?
- **Irrevocability vs. CARE:** is "tombstone + propagation notice" enough, or does community knowledge
  need a fundamentally more revocable default than open CC allows?
- **Reviewer equity:** how are origin-community cultural reviewers compensated and credited so review is
  not itself extractive? (Plan flags it; no funding model yet.)
- **FPIC authority verification:** who legitimately consents for a "community," and how is that verified
  without imposing an outside definition? (Plan's own top open question — unresolved.)
- **Restricted-knowledge edge cases:** what if a recipe is contested *between* community factions, or an
  individual contributes a recipe the community considers restricted?
- **Steward:** still TO BE SECURED — blocks "shipped." NĀTIFS-style sovereignty orgs, SFA/UNC, or a
  diaspora association are the strongest candidate profiles surfaced by this research.

---

### Sources
- Local Contexts / TK Labels: https://localcontexts.org/labels/traditional-knowledge-labels/
- CARE Principles (GIDA): https://www.gida-global.org/careprinciples ; https://datascience.codata.org/articles/10.5334/dsj-2020-043
- Wikibooks Cookbook: https://en.wikibooks.org/wiki/Cookbook:Table_of_Contents ; license: https://enterprise.wikimedia.com/project-data/wikibooks-api/
- schema.org/Recipe: https://schema.org/Recipe
- Internet Archive cookbooks: https://archive.org/details/cbk ; https://www.openculture.com/2022/10/10000-vintage-recipe-books-are-now-digitized-by-the-internet-archive.html
- UNC Southern Foodways / Oral History: https://guides.lib.unc.edu/southern-foodways/Archival
- MSU Feeding America / NYU Food Studies: https://lib.msu.edu/murray-hong-spc/cookery ; https://guides.nyu.edu/foodstudies/special-collections
- Whetstone / diaspora foodways: https://www.whetstonemagazine.com/journal/venezuelan-cuisine-finds-rebirth-in-diaspora
- NĀTIFS / Sean Sherman / Indigenous food sovereignty: https://natifs.org/ ; https://seansherman.com/ ; https://www.usda.gov/about-usda/general-information/staff-offices/office-tribal-relations/programs-and-services/usda-indigenous-food-sovereignty-initiative
- Recipe copyright (Publications Int'l v. Meredith): https://copyrightalliance.org/are-recipes-cookbooks-protected-by-copyright/
- Cooklang spec: https://cooklang.org/docs/spec/
- Family-recipe apps: https://heirloomrecipebox.app/ ; https://www.familycookbookproject.com/
