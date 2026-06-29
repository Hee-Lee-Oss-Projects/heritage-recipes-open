# PLAN — heritage-recipes-open

> Status: Draft · Version: 0.1.0 · Last updated: 2026-06-28 · Owner: TBD (maintainer) · Lane: donated

An open, structured, **consent-first** dataset of traditional and regional recipes — each one
carrying its origin community, the tradition-bearer who shared it, documented permission to publish,
source provenance, allergen and food-safety metadata, and a clear open license (CC-BY-4.0 by
default). Built so cultural food knowledge is preserved *with* communities, attributed to them, and
revocable by them — never extracted from them.

## Executive summary

Traditional and regional recipes are a fragile, living form of cultural heritage. They are carried in
the memory of elders and home cooks, scattered across out-of-print community cookbooks, oral history,
and family notebooks. When a tradition-bearer passes without recording a dish, that knowledge is lost.
Where recipes *do* exist online they are typically locked in ad-heavy proprietary sites, copyrighted
modern cookbooks, or unstructured prose — not machine-readable, not openly licensed, not attributed to
the communities they came from, and not preservable.

This project builds an **openly-licensed, structured recipe dataset** (schema.org/Recipe + JSON-LD,
with Cooklang and Open Recipe Format exports) in which **every recipe carries (a) documented consent
from the contributor/community to publish under the stated license, (b) cultural attribution to the
originating tradition and community, (c) source provenance, (d) structured ingredients, steps,
quantities (metric + local units), and (e) allergen and food-safety metadata.** A lightweight
explorer and standard exports make the corpus usable by educators, cultural organizations, diaspora
communities, researchers, and downstream open projects (Wikimedia, open recipe tools).

The headline constraints — and the project's identity — are **consent, cultural attribution, and
licensing**, not volume. Recipes are not just data; for many communities they are heritage and, in
some cases, restricted or sacred knowledge. The project adopts the **CARE Principles for Indigenous
Data Governance** (Collective benefit, Authority to control, Responsibility, Ethics) alongside FAIR,
supports **Traditional Knowledge (TK) Labels** (Local Contexts), and treats **a contributor's right to
withdraw a recipe as a first-class, propagating operation.** No recipe is published without a recorded
consent decision — enforced as a CI gate, exactly as un-sourced data is rejected in the project's
provenance model.

Risk tier: **low** overall (open culinary content). **But two narrow bands are escalated:** recipes
touching **food-safety-critical techniques** (home canning, fermentation, curing/charcuterie, raw
dairy/eggs, wild foraging, infant food) are treated as **medium risk** and require food-safety review
against authoritative guidance with a "not a substitute for tested guidance" disclaimer; and
**translations** of recipes are **medium** (domain-accuracy review). Health/medicinal claims about
foods ("cures," "detoxes," "boosts immunity") are stripped or flagged as non-advice.

A **named partner / steward community is TO BE SECURED.** The need (cultural-knowledge loss; absence
of an open, attributed, consent-grounded corpus) is real, but a committed last-mile beneficiary that
adopts and co-governs the dataset has not yet signed on. Securing one is a first-class M0/M1
objective and a precondition for declaring the project *shipped*.

## Problem & beneficiaries

**The problem.** Traditional foodways are disappearing faster than they are being recorded. The
recipes that survive online are mostly (1) behind ads/paywalls on for-profit sites, (2) inside
in-copyright modern cookbooks, (3) unstructured prose that machines can't parse, or (4) stripped of
the community, person, and story that give them meaning. There is no widely-used **open, structured,
consent-grounded, attributed** corpus of heritage recipes. Naive "open recipe scraping" projects make
the problem worse: they launder copyrighted text and erase cultural attribution and consent.

**Beneficiaries.**
- **Tradition-bearers and origin communities** — elders, home cooks, diaspora and Indigenous
  communities — who want their foodways preserved, attributed, and on *their* terms.
- **Diaspora and second-generation families** seeking to recover ancestral dishes.
- **Educators and cultural organizations** (community kitchens, heritage museums, libraries, language-
  revitalization programs) needing free, trustworthy, attributable teaching material.
- **Researchers** (food studies, anthropology, public health/nutrition, linguistics) needing
  structured, citable data with provenance.
- **Downstream open projects** — Wikimedia/WikiProject Food, open recipe tools (Cooklang, Open Recipe
  Format), accessibility and translation projects — that can reuse a clean, licensed corpus.
- **The public / cultural commons** — a durable, open record of human foodways.

**Verified need.** The *gap* (no open, attributed, consent-first heritage-recipe corpus) is real and
demonstrable. However, a **named partner organization or steward community that will co-govern, adopt,
and cite the output is TO BE SECURED.** Tasks therefore carry `verifiedNeed: false` until a committed
partner is named. Per the quality bar ("delivered, not merged"), securing this partner is an
M0/M1 objective and a precondition for *shipped*. Critically — because the dataset is *about*
communities — partner engagement is not only a last-mile concern but an **upstream ethics
requirement**: communities must have authority over their own data from the start (CARE).

**Partner org.** TO BE SECURED. Candidate stewards: a cultural-heritage museum or folklife center; a
community kitchen or diaspora association; a public library's local-history/special-collections team; a
language-revitalization program; Wikimedia affiliates; or an academic food-studies department. At
least one community partner with **authority to consent on behalf of a community-level tradition** is
required before any community-attributed (as opposed to individually-contributed) recipe is published.

## Goals and non-goals

**Goals**
- Publish an **openly-licensed, structured** heritage-recipe dataset with **consent, cultural
  attribution, and provenance on every recipe** (each enforced as a hard gate).
- Define a reusable **schema** extending schema.org/Recipe with heritage fields (origin community,
  tradition, tradition-bearer/attribution, consent record, TK labels, provenance, allergens,
  food-safety flags), interoperable with Cooklang and Open Recipe Format.
- Operate a **consent-first contribution workflow** (including Free, Prior, and Informed Consent for
  community-level knowledge) with a working **right-to-withdraw** that propagates to downstream mirrors.
- Normalize ingredients and quantities (metric + local/customary units) while **preserving original
  names, language, and technique** faithfully — heritage fidelity over standardization.
- Attach **allergen metadata** and **food-safety notes from authoritative sources** to every recipe;
  escalate safety-critical categories to expert review.
- Secure at least one **community/cultural steward** that co-governs and adopts the dataset.
- Ship a simple public **explorer** and standard **exports** (JSON-LD, Cooklang, ORF, CSV).

**Non-goals**
- **Not** a scrape or mirror of for-profit recipe sites or in-copyright cookbooks. Copying protected
  recipe *expression* (headnotes, photos, prose) is out of scope and never acceptable.
- **Not** a recipe corpus published *without* a recorded consent decision and cultural attribution.
- **Not** a holder of restricted/sacred knowledge: recipes a community designates as not-for-publication
  are recorded as restricted and **not published**.
- **Not** a source of medical/nutritional or health advice; medicinal/health claims are stripped or
  flagged as non-advice with an expert-review gate if retained as documented cultural belief.
- **Not** authoritative food-safety guidance; safety notes point to tested authorities (e.g. USDA/
  NCHFP) and carry a "not a substitute for tested guidance" disclaimer.
- **Not** a general social cooking platform, user-account system, ad business, or for-profit product.
- **Not** a collector of contributor PII beyond the minimum needed for attribution and consent; **no
  data from minors** as contributors/subjects.
- **Not** an arbiter of "authenticity" that flattens regional variation; variants are recorded, not
  ranked.

## Success metrics (outcomes)

Outcome-based and beneficiary-centric. Baselines are zero at project start unless noted. We explicitly
**do not** treat raw recipe count, PRs merged, or commits as success — a large corpus with weak consent
or attribution is a **failure** under this plan.

| Metric | Baseline | Target (first 12 months) |
| --- | --- | --- |
| Recipes published with a complete, valid **consent record** | 0 | 100% (hard gate — no consent record, no publication) |
| Recipes published with **cultural attribution** (community + tradition + bearer/source) | 0 | 100% (hard gate) |
| Recipes carrying **resolvable source provenance** | 0 | 100% (hard gate) |
| Recipes with **allergen metadata** populated (incl. explicit "contains none of the major allergens" or "unknown") | 0 | 100% (hard gate) |
| Safety-critical recipes (canning/fermentation/curing/raw/foraging/infant) passing **food-safety review** before publish | n/a | 100% (hard gate for that band) |
| **Right-to-withdraw** requests honored within SLA, with downstream-mirror propagation notice | n/a | 100% within 7 days; propagation notice issued ≤ 48h |
| Distinct **origin communities/traditions** represented, *each with documented consent path* | 0 | ≥ 5 communities, ≥ 100 recipes total (consent + attribution + provenance complete) |
| Fidelity audit: sampled recipes verified faithful to source / approved by the tradition-bearer | n/a | ≥ 95% of a **stratified** audit sample (frame below) |
| Translations passing **domain-accuracy review** (where translations exist) | n/a | 100% reviewed; ≥ 95% accepted by a fluent reviewer |
| Committed community/cultural **steward(s)** co-governing & adopting the dataset | 0 | ≥ 1 committed steward; ≥ 1 documented downstream citation/use |
| Tradition-bearer satisfaction (post-publication check-in: "represented fairly?") | n/a | ≥ 90% "yes/mostly" among contributors surveyed |
| Reuse: external downloads / exports / downstream integrations | 0 | tracked from M2; quarterly trend reported |

**Fidelity-audit sampling frame (pins the data-quality metric).** The ≥95% target uses: a **minimum
sample size** of 50 recipes per release (or the whole release if smaller); **stratified sampling**
across strata defined by *origin community* and by *contribution method* (direct interview/contribution
vs. PD-source transcription vs. openly-licensed import), so no community or method escapes review; an
**auditor independent of the contributor/transcriber** of the sampled records; and, for
directly-contributed recipes, a **back-to-the-source check** — the tradition-bearer confirms the
published version represents what they shared. Safety-critical and translated recipes are audited at
**100%**, not sampled.

## Scope

**In scope**
- Schema definition (heritage extensions over schema.org/Recipe) and a per-source/per-contribution
  **consent + license + provenance** record format.
- A **consent-first contribution workflow** (individual contribution and community FPIC paths).
- Structured capture of recipes: title (original + translated), origin community/region, tradition,
  attribution/bearer, ingredients, quantities (metric + local), steps, technique notes, allergens,
  food-safety flags, story/headnote (contributor-authored, openly licensed), media (licensed
  separately).
- Ingestion of **public-domain** and **openly-licensed** recipe sources (e.g. PD community cookbooks,
  CC-licensed collections, government/extension materials) with per-item rights verification.
- Translations (original language + translation, translator credited, fidelity review).
- Allergen tagging and food-safety annotation from authoritative sources.
- Right-to-withdraw tooling, TK Labels, and downstream-propagation notices.
- Explorer + exports (JSON-LD, Cooklang, ORF, CSV) and outreach for a community steward.

**Out of scope (explicit)**
- **Any scraping, bulk copying, or re-publication of for-profit recipe sites or in-copyright cookbook
  text/photos.** A hard refusal under Elyos guardrails, not a deprioritized item.
- **Publishing any recipe without a recorded consent decision and cultural attribution.**
- **Restricted/sacred knowledge** a community asks not to publish (recorded as restricted; never
  published).
- Medical, nutritional, therapeutic, or health advice; "this food cures/treats X" claims.
- Authoritative food-safety instructions presented as tested/validated (we annotate and *refer to*
  authorities; we do not certify safety).
- Contributor PII beyond minimal attribution/consent; any data from minors.
- Accounts, social features, ads, monetization, or "authenticity" rankings.
- AI-invented recipes, ingredients, or cultural attributions; gaps stay gaps.

## Solution approach & architecture

A **data/content pipeline** project (with supporting tooling), not a hosted service.

**Pipeline stages**
1. **Intake & eligibility gate.** Every contribution or source is logged with a machine-readable record
   capturing: contribution method (direct contribution / PD transcription / openly-licensed import),
   **consent record** (who consented, to what license, with right-to-withdraw acknowledged; for
   community knowledge, an FPIC record naming the authority who consented), **license/PD basis**, source
   provenance, and `status: approved | rejected | pending | restricted`. Nothing is processed past
   `pending`; `restricted` recipes are recorded but **never published**.
2. **Schema layer.** A documented schema (`schema/`) extending **schema.org/Recipe** with heritage
   fields, published as JSON Schema + SHACL + a human-readable spec. Defines the **countable units** the
   CI gates measure: one *recipe record* must carry exactly one consent record, one attribution block,
   one provenance link, and an allergen field (possibly "unknown").
3. **Capture & structuring.** Contributions are turned into typed recipe records: ingredients and
   quantities normalized (metric + original/customary units retained), steps structured, **original
   names and language preserved**. Capture is **assistive**; ambiguous quantities, unfamiliar
   ingredients, or unclear techniques are **flagged for human/tradition-bearer confirmation, never
   guessed**.
4. **Cultural attribution & TK Labels.** Each recipe is bound to its origin community/tradition and
   bearer/source, with **TK Labels** (Local Contexts) applied where a community requests them.
5. **Allergen & food-safety annotation.** Allergen tags applied (major allergen classes + "unknown");
   safety-critical techniques detected and **escalated to food-safety review** with authoritative
   references and the "not a substitute for tested guidance" disclaimer. Health/medicinal claims are
   stripped or flagged as documented-belief (non-advice).
6. **Translation (optional).** Original-language text retained; translation added with translator
   credit and **fluent-reviewer fidelity check**.
7. **Validation (CI gates).** Schema validation + **consent-completeness**, **attribution-completeness**,
   **provenance-completeness**, and **allergen-presence** linters. CI rejects: any recipe missing a
   consent/attribution/provenance/allergen unit; any recipe whose source isn't `approved`; any
   `restricted` recipe in the publish set; any safety-critical recipe lacking food-safety sign-off.
8. **Publish.** Versioned exports (JSON-LD, Cooklang, ORF, CSV) under stable, host-independent
   identifiers, plus a simple explorer. **Withdrawals** remove the recipe and emit a tombstone +
   downstream-propagation notice.

**Tech stack**
- Tooling/validators/exporters: **TypeScript, ESM, pnpm** (Elyos conventions).
- Recipe modeling: **schema.org/Recipe** core + heritage extension; serialized as **JSON-LD**; interop
  exports to **Cooklang** and **Open Recipe Format**; **CSV** for researchers.
- Validation: **JSON Schema + SHACL** shapes + custom consent/attribution/provenance/allergen linters
  in CI.
- Identifiers: host-independent persistent IDs (w3id.org/PURL) per recipe and per community/tradition.
- Explorer: static-site explorer over JSON-LD — no accounts, no visitor PII.

**Data model (core record: `Recipe`, extending `schema:Recipe`)**
- **title** (original-language) + **titleTranslated[]** (with language tag).
- **originCommunity / region / tradition** (each a referenceable entity with persistent ID).
- **attribution** — tradition-bearer or source, as the community/contributor wishes to be credited
  (may be a named person *with consent*, a family, a community, or "anonymous by request").
- **consentRecord** — consenter identity/role, license granted, FPIC flag for community knowledge,
  right-to-withdraw acknowledgement, date, and consent artifact reference. **Required.**
- **provenance** — source (interview, PD book + page, openly-licensed import + link) with license/PD
  basis. **Required.**
- **ingredients[]** — name (original + normalized), quantity (value + unit, metric + customary),
  notes; **allergenTags** at recipe level (major allergen classes, or `unknown`). **Required field.**
- **steps[]** — ordered, structured technique steps; original technique terms retained.
- **safetyFlags[]** + **safetyNotes** — for canning/fermentation/curing/raw/foraging/infant; with
  authoritative references and disclaimer.
- **tkLabels[]** — Traditional Knowledge Labels where requested.
- **media[]** — images/audio with **independent** license records (often the licensing trap).
- **license** — per-recipe (default **CC-BY-4.0**; CC0 where purely PD-derived; community may request a
  TK Label overlay or a more restrictive published status, including restricted/not-published).

**Key decisions (to ratify in M0)**
- **Consent is a hard, countable gate**, modeled identically to provenance: one consent record per
  published recipe; CI rejects any recipe without one. (This is the project's headline control.)
- **Schema profile:** schema.org/Recipe as the base (maximizing downstream reuse), with a documented
  heritage extension and round-trippable Cooklang/ORF exports.
- **Identifier scheme:** host-independent persistent IDs (w3id.org/PURL), decoupled from the (unsecured)
  steward, so recipe/community IDs stay stable and the corpus is never orphaned.
- **Variant policy:** regional/family variants are co-equal records linked as variants — no single
  "authentic" winner.
- **Withdrawal semantics:** a withdrawn recipe is removed and replaced by a tombstone; a propagation
  notice is published so downstream mirrors can comply (the license is irrevocable for copies already
  distributed, which is disclosed to contributors up front — see compliance section).

## Data, licensing & compliance

**This is a headline gate for the project (alongside consent). Read before doing any data work.**

### Copyright nuance — what is and isn't protected in a recipe
In many jurisdictions (notably the U.S.), a **bare list of ingredients and a purely functional
procedure are facts/processes and not protected by copyright**, while the **literary expression**
around a recipe — headnotes, descriptive prose, stories, photographs, and creative selection/
arrangement of a *collection* — **is** protected. The project treats this conservatively:
- We do **not** copy protected expression (headnotes, prose, photos) from in-copyright sources.
- Imported *facts* (ingredients/steps) from a copyrighted source are still **out of scope by default**,
  because (a) jurisdictions differ, (b) a compilation can carry its own copyright, and (c) site Terms
  of Service can independently bar copying. We rely on **directly-contributed**, **public-domain**, or
  **openly-licensed** sources instead.
- All contributor-authored expression (stories, headnotes, photos) is licensed **inbound** by the
  contributor under the project license via an explicit consent/contributor-license step.

### Consent — the primary ethical and legal gate
Because recipes are tied to living people and communities, **consent is mandatory and recorded**:
- **Individual contributions:** the contributor consents to publication under the stated license,
  chooses how to be attributed (named / family / community / anonymous), and **acknowledges the
  right-to-withdraw terms** (including that copies already distributed under an open license cannot be
  recalled — disclosed plainly *before* contributing).
- **Community-level / Indigenous knowledge:** a **Free, Prior, and Informed Consent (FPIC)** record is
  required, naming the community authority who consented, per the **CARE Principles**. Without it, the
  recipe is `pending` or `restricted` — never published.
- **Restricted/sacred knowledge:** if a community designates a recipe as not-for-publication, it is
  recorded as `restricted` and **never published**, in any export.

### Approved sources (consent-backed, public-domain, or openly licensed only)
Every source/contribution is entered with a recorded basis and `approved` status before use:
- **Direct contributions** from tradition-bearers/home cooks **with a consent record** (primary path).
- **Public-domain cookbooks/collections** (e.g. copyright-expired editions; U.S. generally pre-1929 —
  verify each edition; government/extension materials that are PD).
- **Openly-licensed collections** (CC-BY / CC-BY-SA / CC0) — license verified per item, attribution
  obligations recorded; share-alike (CC-BY-SA) material is segregated and labeled.
- **Reference vocabularies** (schema.org; Wikidata CC0 for ingredient/place reconciliation).

**Caveats we will not gloss over:** a public-domain *text* can be wrapped in a copyrighted **scan,
photo, or modern translation**; "openly licensed" must be verified for the *specific item and media*
used. **Photos are a frequent trap** and are licensed/verified independently of the recipe text.

### Provenance & attribution model
- **Every published recipe** carries: a consent record, a cultural-attribution block, and a source
  provenance link with its license/PD basis. These are CI-enforced over the countable recipe unit.
- Un-consented, un-attributed, or un-sourced recipes are **never published**.
- Variants retain their own provenance; no merging that erases a community's version.

### Privacy / PII stance
- Collect the **minimum** contributor PII needed for attribution and consent; honor "anonymous by
  request"; store consent artifacts securely and never in public exports beyond what was consented.
- **No data from minors.** No third-party living persons named without their consent.
- Right-to-withdraw covers both the recipe and the contributor's personal data in project-controlled
  surfaces.

### Attribution & output license
- **Code:** MIT. **Data/content default:** **CC-BY-4.0** (attribution to the community/bearer as they
  chose). **CC0** where purely PD-derived and the contributor opts in. **CC-BY-SA-4.0** where SA
  material is incorporated (segregated + labeled). **TK Labels** may overlay any license as a
  non-legal cultural notice; `restricted` items are excluded entirely.
- Required attributions (community/bearer credit, CC-BY upstream credit, photo credits) are recorded
  and surfaced in every export.

## Quality, review & risk gates

**Risk tier: low overall, with escalated bands.** Review dimensions, all required before a deed is
"done":

1. **Consent & licensing review (primary gate).** A reviewer confirms each contribution/source has a
   valid consent record (FPIC for community knowledge), an approved license/PD basis, and is not copied
   from a proprietary/in-copyright source. No capture task starts against a `pending`/`rejected` source;
   any task proposing to scrape a for-profit/in-copyright source is **refused and flagged**.
2. **Cultural-fidelity & attribution review (medium for community knowledge).** A reviewer with
   relevant cultural/domain knowledge — ideally from or endorsed by the origin community — confirms the
   recipe and attribution faithfully represent what was shared; "authenticity flattening" and erased
   attribution block sign-off.
3. **Food-safety review (medium; mandatory for the safety-critical band).** Recipes involving home
   canning, fermentation, curing/charcuterie, raw dairy/eggs, wild foraging, or infant food require a
   reviewer with food-safety competence to confirm safety notes reference authoritative tested guidance
   (e.g. USDA/NCHFP) and carry the "not a substitute for tested guidance" disclaimer. Health/medicinal
   claims are stripped or marked documented-belief (non-advice).
4. **Translation review (medium; where translations exist).** A fluent reviewer confirms translation
   fidelity; the original-language text is always retained.

**Definition of Shipped (project level).** A published, openly-licensed, structured recipe dataset
with: **100% consent + attribution + provenance + allergen** coverage; ≥5 communities and ≥100 recipes
with complete records; safety-critical and translated recipes reviewed at 100%; a **working
right-to-withdraw** demonstrated end-to-end; passing CI gates; explorer + exports live; and **at least
one community/cultural steward that has adopted/co-governs and cited** the dataset. Per Elyos,
*delivered ≠ merged* — the corpus must be in beneficiaries' hands and communities must affirm fair
representation.

**Per-deed Definition of Done.** Acceptance criteria met + CI green (schema/consent/attribution/
provenance/allergen) + consent & licensing review passed + cultural-fidelity review passed (+
food-safety sign-off for the safety band, + translation review where applicable) + output published
under the declared license.

## Roadmap & milestones

**M0 — Foundation, consent & licensing spine (cold-start).**
Goal: build the rails so no recipe can be published without consent, attribution, provenance, and an
allergen field.
Exit criteria: (a) heritage schema v0 published (schema.org/Recipe extension; JSON Schema + SHACL +
spec) defining the countable consent/attribution/provenance/allergen units; (b) consent + license +
provenance record format defined, **including the FPIC path for community knowledge and the
restricted/not-published status**; (c) CI scaffolded for consent-, attribution-, provenance-, and
allergen-completeness + schema validation; (d) right-to-withdraw + TK-Label design specified;
(e) safety-critical taxonomy + food-safety-reference policy + non-advice/health-claim policy drafted;
(f) host-independent persistent-ID scheme committed; (g) partner/steward and community outreach started
(status logged); (h) **a qualified consent/licensing reviewer named** (hard exit; documented fallback
if the seat is empty — M0 cannot exit and escalation begins). 
Dependencies: none.

**M1 — First consented slice (proof of pipeline).**
Goal: take one community's recipes end-to-end with full consent, attribution, provenance, allergens,
and (if applicable) safety review.
**Hard entry precondition:** a consent path for the M1 community is in place — either signed individual
consents or an FPIC record from a community authority — recorded as `approved` before capture begins.
Exit criteria: (a) ≥10 recipes from one community captured into valid records; (b) 100% carry consent +
attribution + provenance + allergen and pass CI; (c) any safety-critical/translated recipes pass 100%
review; (d) **fidelity audit** (stratified; independent auditor; back-to-source check) ≥95% verified;
(e) JSON-LD + one interop export (Cooklang or ORF) produced under the persistent-ID scheme;
(f) right-to-withdraw exercised successfully in a test (recipe removed + tombstone + propagation
notice); (g) ≥1 candidate steward in conversation. Depends on M0.

**M2 — Usable surface (explorer, exports, reuse).**
Goal: make the corpus discoverable, reusable, and safely consumable.
Exit criteria: (a) public explorer live (no accounts/PII) showing each recipe's attribution, consent
status, provenance, allergens, and safety notes; (b) documented exports (JSON-LD, Cooklang, ORF, CSV)
with attribution/license metadata; (c) ingredient/place reconciliation to Wikidata (assistive,
human-confirmed); (d) reuse metrics tracked; (e) contributor satisfaction check-in mechanism live.
Depends on M1.

**M3 — Scale, multi-community & steward adoption (shipped).**
Goal: broaden communities and lock in real-world, community-affirmed use.
Exit criteria: (a) ≥5 communities and ≥100 recipes with complete records; (b) ≥1 steward has
**adopted/co-governs and cited** the dataset (Definition of Shipped met); (c) tradition-bearer
satisfaction ≥90% among surveyed contributors; (d) sustainability/maintenance + reviewer-rotation plan
in effect; (e) right-to-withdraw SLA demonstrably met in production. Depends on M2.

## Work breakdown

The itemized, schema-mapped backlog lives in [`TASKS.md`](./TASKS.md), organized by the milestones
above (M0–M3) plus a sized backlog. Each task maps to an Elyos Task JSON and carries a type, size,
risk tier, deliverable, dependencies, and reviewer. M0 deliberately front-loads consent, licensing,
attribution, allergen, and safety guardrails **before any recipe is captured at scale.**

## Governance, roles & stakeholders

- **Maintainer / Owner:** TBD — accountable for scope, the consent/licensing gate, and releases.
- **Consent & licensing reviewer:** TBD — must approve every contribution/source record; veto over any
  source; owns the right-to-withdraw process. **Naming a qualified person is a hard M0 exit
  criterion.** **Fallback if empty:** nothing advances past `pending`; no capture begins; maintainer
  escalates to Elyos governance/board (and may engage pro-bono counsel) before any data work.
- **Cultural-fidelity reviewers (rotation):** people with relevant cultural/domain knowledge — ideally
  **from or endorsed by each origin community** — performing attribution/fidelity review. TO BE SECURED
  per community.
- **Food-safety reviewer:** TBD — required for the safety-critical band (medium risk); confirms
  authoritative referencing and disclaimers.
- **Translation reviewers:** fluent speakers per language pair. TO BE SECURED as needed.
- **Community steward(s) / last-mile owner:** the cultural org/community that adopts, co-governs, hosts
  long-term, and cites the dataset. **TO BE SECURED** — required for "shipped." Communities hold
  **authority over their own data** (CARE) including withdrawal.
- **Partner / requestor:** diaspora/heritage communities, educators, researchers (diffuse beneficiary
  class); a named representative steward is TO BE SECURED.
- **Elyos governance/board:** arbiter for edge cases (e.g. a borderline source, an attribution dispute,
  a restricted-knowledge claim) under the published conflict-of-interest/veto checklist.

## Dependencies & integrations

- **schema.org/Recipe** vocabulary; **Cooklang** and **Open Recipe Format** specs (export interop).
- **Local Contexts / TK Labels** (cultural attribution overlay).
- **CARE Principles for Indigenous Data Governance** and **FAIR** (governance frameworks).
- **Authoritative food-safety references** (e.g. USDA / National Center for Home Food Preservation) —
  *referenced*, not republished as our own guidance.
- **Wikidata** (CC0) for ingredient/place reconciliation.
- **SHACL / JSON-Schema tooling**, an RDF/JSON-LD library (TypeScript/ESM).
- **Elyos pieces:** Task schema (`packages/schema`), CLI workspace/PR flow (`packages/cli`,
  `packages/core`), governance proposal/registry process. **Donated lane** — humans run their own
  agents; the CLI never runs headless or authenticates an agent.
- **Steward host** (TO BE SECURED) for long-term hosting; persistent IDs stay project-owned regardless.

## Risks & mitigations

| Risk | Likelihood | Impact | Mitigation | Owner |
| --- | --- | --- | --- | --- |
| Recipe published without valid consent (esp. community/Indigenous knowledge) | Medium | Critical (ethical/legal, project-ending) | Consent is a hard CI gate (no record → not published); FPIC required for community knowledge; consent/licensing reviewer veto; restricted status honored; refuse + flag per guardrails | Consent/licensing reviewer |
| Copyrighted cookbook/site text or photos copied (incl. laundered) | Medium | High (copyright/ToS) | Direct/PD/openly-licensed sources only; protected expression never copied; **photos licensed independently**; per-item/edition rights check; reviewer veto; CI rejects non-`approved` sources | Consent/licensing reviewer |
| Cultural misappropriation / erased or wrong attribution | Medium | High | Mandatory cultural-attribution gate; reviewers from/endorsed by the community; CARE + TK Labels; variants co-equal (no "authenticity" ranking); satisfaction check-in | Cultural-fidelity reviewer |
| Unsafe food-safety guidance (canning/fermentation/raw/foraging/infant) causes harm | Low | Critical (health/safety) | Safety-critical band → medium risk, 100% food-safety review; authoritative references + "not a substitute for tested guidance" disclaimer; health claims stripped/flagged | Food-safety reviewer |
| Missing/incorrect allergen information harms a consumer | Medium | High | Allergen field is a hard CI gate (incl. explicit "unknown"); major-allergen tagging; disclaimer that users must verify for their own allergies | Maintainer + food-safety reviewer |
| No steward/community partner secured → "delivered ≠ merged" unmet | High | High | Partner/community outreach as M0/M1 deliverable; honest `verifiedNeed:false`; multiple candidate stewards; maintained-but-not-shipped honesty if none | Maintainer |
| Contributor withdraws but copies persist downstream | Medium | Medium | Disclose irrevocability of distributed open copies *before* contributing; remove from project surfaces + tombstone + downstream propagation notice within SLA | Consent/licensing reviewer |
| Inaccurate/invented recipe details or "smoothed" technique | Medium | Medium | Assistive (not autonomous) capture; flag-on-doubt; back-to-source fidelity audit; gaps stay gaps | Cultural-fidelity reviewer |
| Health/medicinal food claims presented as advice | Medium | High | Strip or mark as documented cultural belief (non-advice); expert gate if retained; explicit non-advice policy | Food-safety reviewer |
| Translation distorts meaning/technique | Medium | Medium | Retain original language; fluent-reviewer fidelity check; translations audited 100% | Translation reviewer |
| Reviewer capacity exhausted (consent + cultural + safety review bottleneck) | Medium | High | Sampling-based fidelity review; reviewer rotation + response-time SLA; documented throughput ceiling throttling intake when backlog exceeds it | Maintainer |
| Contributor PII or minors' data collected | Low | High (privacy) | Minimal-PII policy; no minors; "anonymous by request"; consent artifacts stored securely, excluded from public exports | Consent/licensing reviewer |
| Persistent-ID/host instability orphans the corpus | Low | Medium | Project-owned w3id.org/PURL IDs decoupled from steward host; redirect strategy | Maintainer |
| Scope creep into a social/ad recipe platform | Medium | Medium | Explicit non-goals; governance review of scope changes | Maintainer |

## Security & privacy

- **Threat surface:** small (data/content project; no accounts; no visitor PII in the explorer). The
  real risks are *ethical/compliance* (un-consented or misappropriated knowledge, copyright) and *data
  integrity* (unsafe or inaccurate recipes), addressed by the consent, licensing, fidelity, and
  food-safety gates above.
- **Secrets handling:** no API keys needed for the public/contributed sources; any reconciliation
  credentials stay out of logs, receipts, and commits per Elyos rules. The donated lane never runs
  headless or authenticates an agent. Consent artifacts containing PII are stored in a controlled,
  non-public location — **never committed to the repo or included in exports.**
- **PII:** minimal contributor data, consent-bound; no minors; "anonymous by request" honored;
  right-to-withdraw covers personal data in project-controlled surfaces.
- **Abuse/misuse prevention:** every recipe is consent- and source-linked so claims/attributions are
  auditable; the project refuses and flags scraping of proprietary sources, publication of restricted
  knowledge, collection of minors' data, and any health-claim/medical-advice framing.

## Sustainability & maintenance

- **After delivery,** the maintainer plus the secured community steward co-own ongoing curation; the
  steward provides long-term hosting while the **persistent IDs remain project-owned**, so recipe and
  community identifiers survive a steward change and the corpus is never orphaned.
- **Community authority is ongoing:** withdrawal and re-attribution requests are honored on an SLA for
  the life of the dataset (CARE — Authority to control is not a one-time event).
- **Reviewer sustainability:** fidelity review runs on **sampling** (safety/translation at 100%);
  reviewers work a **rotation with a response-time SLA**; a **documented throughput ceiling** throttles
  new intake when the review backlog exceeds it, so gates never silently degrade.
- **Outcome tracking:** quarterly report on consent/attribution/provenance/allergen completeness (must
  stay 100%), communities represented, fidelity-audit pass rate, withdrawal SLA adherence, steward
  adoption, contributor-satisfaction, and reuse/downloads.
- **Contributions** continue via the donated lane under the same consent + licensing + fidelity + safety
  gates. **Versioned releases** (with changelogs and a withdrawals log) keep downstream consumers
  stable and compliant.
- If no steward is secured, the project remains in a **maintained-but-not-shipped** state and the gap is
  reported honestly rather than declared done.

## Open questions

- Who is the committed community/cultural **steward**? (TO BE SECURED — blocks "shipped.")
- For each community, who holds **authority to give FPIC** for community-level recipes, and how is that
  verified without imposing an outside definition of "community"?
- Default content license: **CC-BY-4.0** for all, or per-contributor choice among CC-BY / CC0 / CC-BY-SA
  (with SA segregation)? (Leaning CC-BY-4.0 default, contributor-overridable.)
- Exact **safety-critical taxonomy** and which authority's guidance to reference per region (USDA/NCHFP
  in the U.S.; what for other regions?).
- How are **TK Labels** operationalized in JSON-LD exports and in the explorer UI?
- Withdrawal propagation: what concrete mechanism (feed/notice format) do downstream mirrors subscribe
  to?
- Who staffs the **cultural-fidelity reviewer rotation** per community, and how are reviewers
  compensated/credited to avoid extractive volunteer burden?

## References

- Project proposal: `governance/proposals/heritage-recipes-open.md` (TO BE CREATED)
- Elyos work rules: `CLAUDE.md`
- Good Deed Definition & risk tiers: `docs/good-deed-definition.md`
- Task JSON schema: `packages/schema/src/schemas.ts`
- Portfolio roadmap: `planning/ROADMAP.md` (Track 5 — Culture & heritage)
- schema.org/Recipe vocabulary; Cooklang; Open Recipe Format
- Local Contexts — Traditional Knowledge (TK) Labels
- CARE Principles for Indigenous Data Governance; FAIR Principles
- USDA / National Center for Home Food Preservation (food-safety references)
- Wikidata (CC0); Creative Commons CC-BY-4.0 / CC0 / CC-BY-SA-4.0 licenses

---

## Appendix A — Improvements applied

The following 25 specific improvements were identified against the first draft and **are applied
throughout this PLAN and the companion TASKS.md** (not merely listed). Each notes where it lands.

1. **Consent modeled as a hard, countable CI gate** (like provenance) — no consent record, no
   publication. (Exec summary; Solution §7; Quality gates; metrics row 1.)
2. **FPIC path for community/Indigenous knowledge**, distinct from individual consent. (Compliance;
   M0/M1; roles.)
3. **CARE Principles + FAIR adopted explicitly** for cultural data governance. (Exec summary;
   dependencies; sustainability.)
4. **Traditional Knowledge (TK) Labels** (Local Contexts) supported as a cultural overlay on any
   license. (Data model; compliance; open questions.)
5. **Right-to-withdraw made a first-class, propagating operation** with tombstone + downstream notice +
   SLA, and irrevocability of distributed copies disclosed up front. (Goals; key decisions; metrics;
   risks.)
6. **Restricted/sacred-knowledge status** that is recorded but never published. (Non-goals; pipeline
   status enum; compliance.)
7. **Food-safety band escalated to medium risk** with mandatory expert review for canning/fermentation/
   curing/raw/foraging/infant food. (Risk tier; quality gates; M1.)
8. **"Not a substitute for tested guidance" disclaimer** + authoritative references (USDA/NCHFP) for
   safety content. (Compliance; quality gates; references.)
9. **Allergen metadata as a required field** (major allergen classes + explicit "unknown"), CI-gated.
   (Data model; metrics; risks.)
10. **Health/medicinal-claim guardrail** — claims stripped or marked documented-belief (non-advice).
    (Non-goals; pipeline §5; risks.)
11. **Copyright nuance spelled out** (facts/procedure vs. protected expression; compilation copyright;
    ToS), with conservative default of not importing facts from copyrighted sources. (Compliance.)
12. **Photos/media licensed independently** of recipe text (the common licensing trap). (Data model;
    compliance; risks.)
13. **Inbound contributor licensing step** for contributor-authored expression (stories/headnotes/
    photos). (Compliance.)
14. **Variant policy (no "authenticity" winner)** — regional/family variants co-equal and linked.
    (Non-goals; key decisions; risks.)
15. **Original language always retained**; translations are additive with translator credit and fluent
    fidelity review (medium). (Goals; quality gates; metrics.)
16. **Stratified fidelity-audit frame pinned** (≥50/release, by community & method, independent
    auditor, back-to-source check; safety/translation at 100%). (Success metrics.)
17. **Host-independent persistent IDs** (w3id.org/PURL) for recipes and communities, decoupled from the
    unsecured steward. (Key decisions; sustainability.)
18. **schema.org/Recipe base + Cooklang/ORF interop exports** for maximum downstream reuse. (Stack; key
    decisions; M2.)
19. **No minors' data; minimal PII; "anonymous by request"; consent artifacts never committed/exported.**
    (Privacy; security; risks.)
20. **Reviewer-sustainability controls** — sampling, rotation + SLA, throughput ceiling — to prevent
    extractive volunteer burnout. (Sustainability; risks; metrics.)
21. **Community-endorsed reviewers** preferred for cultural-fidelity review (not outside graders alone).
    (Roles; quality gates.)
22. **Tradition-bearer satisfaction metric** (fair-representation check-in) added as a real outcome.
    (Success metrics; M3.)
23. **Hard M0 exit on a named consent/licensing reviewer**, with documented escalation fallback if the
    seat is empty. (M0; roles.)
24. **Honest `verifiedNeed:false`** until a partner is secured, and a **maintained-but-not-shipped**
    honest end-state. (Problem; sustainability; TASKS mapping.)
25. **Outcome-based metrics only** (consent/attribution/provenance/allergen completeness, communities,
    fidelity, withdrawal SLA, adoption) — raw recipe count explicitly rejected as success. (Success
    metrics intro.)

## Review sign-off

A completeness/correctness review was performed against the Elyos rules, the Good Deed Definition, the
PLAN spec, and the task schema. Findings and resolutions:

- **Measurable metrics:** every success metric has a baseline + target; the fidelity metric has a
  pinned sampling frame; hard gates are at 100%. ✔
- **Enforceable gates:** consent, attribution, provenance, and allergen are CI-enforced over a defined
  countable recipe unit; safety-critical and translated recipes are reviewed at 100%. ✔
- **Risks with owners + mitigations:** 14-row table; every row has an owner and a concrete mitigation;
  the top ethical risk (un-consented community knowledge) is rated Critical with a hard gate. ✔
- **License/PII/expert-review guardrails:** copyright nuance, photo-independent licensing, consent/FPIC,
  no-minors/minimal-PII, food-safety expert gate, and health-claim non-advice policy all present and
  conservative. ✔
- **Sequencing:** M0 front-loads all guardrails before scale capture; M1 requires a consent path as a
  hard entry precondition; M3 ties "shipped" to a real, community-affirmed steward adoption. ✔
- **Schema-valid tasks:** TASKS.md maps every field of `taskSchema`; the example Task JSON validates
  (all required fields present, enum values legal, `verifiedNeed:false`, `outputLicense` set). ✔
- **Honesty:** partner/steward and per-community FPIC authority are marked **TO BE SECURED**;
  `verifiedNeed` is `false`; a maintained-but-not-shipped end-state is acknowledged. ✔

**Open items requiring a human decision:** (1) secure a community/cultural steward and per-community
FPIC authority; (2) ratify the default content license (CC-BY-4.0 vs. per-contributor choice); (3) fix
the safety-critical taxonomy and per-region authoritative references; (4) staff and fairly compensate
the cultural-fidelity reviewer rotation. These are tracked in Open questions and are not resolvable by
the planning agent alone.

Sign-off status: **Draft approved for circulation** — pending the four human decisions above. The plan
is internally consistent and enforceable as written; it does not declare the project shippable until a
steward is secured.
