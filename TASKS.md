# TASKS — heritage-recipes-open

> Status: Draft · Version: 0.1.0 · Last updated: 2026-06-28 · Owner: TBD (maintainer) · Lane: donated

Itemized backlog for the open, consent-first heritage-recipe dataset. See [`PLAN.md`](./PLAN.md) for
context, the consent/licensing gates, the safety/translation escalations, and the roadmap (M0–M3).

## How these tasks map to Hee-Lee Oss

Each task below becomes a Hee-Lee Oss **Task JSON** validated against `packages/schema/src/schemas.ts`.
Field mapping:

- **id** — stable `heritage-recipes-open-<area>-NNN` (the table ID).
- **title** — the table Title.
- **project** — `heritage-recipes-open`.
- **type** — one of `code | research | writing | data | design-spec | maintenance` (table "Type").
- **lane** — `donated` for all tasks here (the proposal's lane). Any future metered run would be
  `funded` and must add `fundedBudgetUsd`.
- **priority** — `high | medium | low`.
- **domain** — e.g. `["culture-heritage","open-data","food","education","language"]`.
- **riskTier** — `low | medium | high`. Most tasks are **low**; **food-safety** capture/annotation and
  **translation** tasks are **medium** (domain-accuracy / safety review). No `high` tasks (no medical
  advice is produced; medicinal claims are stripped, not authored).
- **urgent** — boolean (default `false`).
- **deliverable** — `pr | dataset | document | translation` (table "Deliverable").
- **tokenEstimate** — `small | medium | large` (table "Size").
- **status** — `open | in-progress | review | delivered | done` (start `open`).
- **context / objective / acceptanceCriteria[] / resources[] / output** — per task.
- **requestor** — `jdev1977` / beneficiary class until a named community steward is secured.
- **verifiedNeed** — **`false`** while no committed partner/steward is secured (honest; the *gap* is
  real, the last-mile beneficiary is TO BE SECURED).
- **outputLicense** — `MIT` (code), `CC-BY-4.0` (default data/docs), `CC0-1.0` (purely PD-derived, opt-in),
  or `CC-BY-SA-4.0` (where SA material is incorporated).

> **Standing guardrails on every capture/data task:**
> 1. No recipe is captured or published without an **approved consent record** (FPIC for community
>    knowledge) and a **cultural-attribution block** — both CI-enforced.
> 2. No source is touched until its eligibility record is `approved` (PD / openly-licensed / direct
>    consented). Any task proposing to scrape a for-profit site or copy in-copyright cookbook
>    text/photos is **refused and flagged** — out of scope, full stop.
> 3. **Restricted/sacred** recipes are recorded but **never published**.
> 4. **Safety-critical** recipes (canning/fermentation/curing/raw/foraging/infant) require food-safety
>    review (medium); **translations** require fluent-reviewer review (medium); **health/medicinal
>    claims** are stripped or marked documented-belief (non-advice).

---

## Milestone M0 — Foundation, consent & licensing spine

| ID | Title | Type | Size | Risk | Deliverable | Depends on | Reviewer |
| --- | --- | --- | --- | --- | --- | --- | --- |
| heritage-recipes-open-schema-001 | Define heritage Recipe schema (schema.org/Recipe extension + JSON Schema + SHACL) | design-spec | medium | low | document | — | Maintainer + cultural reviewer |
| heritage-recipes-open-consent-001 | Consent + license + provenance record format (incl. FPIC + restricted status) | design-spec | medium | low | document | — | Consent/licensing reviewer |
| heritage-recipes-open-safety-001 | Safety-critical taxonomy + food-safety-reference + non-advice/health-claim policy | design-spec | small | medium | document | — | Food-safety reviewer |
| heritage-recipes-open-allergen-001 | Allergen taxonomy + required-field policy (major classes + "unknown") | design-spec | small | low | document | heritage-recipes-open-schema-001 | Food-safety reviewer |
| heritage-recipes-open-withdraw-001 | Right-to-withdraw + TK-Label + downstream-propagation design | design-spec | small | low | document | heritage-recipes-open-consent-001 | Consent/licensing reviewer |
| heritage-recipes-open-id-001 | Commit host-independent persistent-ID scheme (w3id.org/PURL) | design-spec | small | low | document | heritage-recipes-open-schema-001 | Maintainer |
| heritage-recipes-open-ci-001 | CI scaffold: schema + consent/attribution/provenance/allergen linters | code | medium | low | pr | heritage-recipes-open-schema-001, heritage-recipes-open-consent-001, heritage-recipes-open-allergen-001 | Maintainer |
| heritage-recipes-open-partner-001 | Community/steward outreach + per-community FPIC-authority mapping | research | small | low | document | — | Maintainer |

**Acceptance criteria (key M0 tasks)**

- **heritage-recipes-open-schema-001**
  - Recipe record defined as a documented extension of schema.org/Recipe, published as JSON Schema +
    SHACL + human-readable spec.
  - Defines the **countable units** the CI gates measure: exactly one consent record, one attribution
    block, one provenance link, and an allergen field per published recipe.
  - Models ingredients/quantities (metric + customary), structured steps, original-language title +
    translations, safety flags, TK labels, media (with independent license slot), and **variant links**
    (no single "authentic" winner).
  - Round-trippable to Cooklang and Open Recipe Format (mapping documented; lossy fields noted).
- **heritage-recipes-open-consent-001**
  - Record format captures: consenter identity/role, license granted, **FPIC flag + community authority
    for community knowledge**, right-to-withdraw acknowledgement (incl. irrevocability of distributed
    open copies, disclosed up front), date, and consent-artifact reference (stored privately, never in
    public exports).
  - Defines `status: approved | rejected | pending | restricted`; **restricted = recorded, never
    published.**
  - States that proprietary/in-copyright sources are categorically `rejected`; protected expression and
    photos are never copied; photos licensed independently.
- **heritage-recipes-open-safety-001**
  - Enumerates the safety-critical band (home canning, fermentation, curing/charcuterie, raw dairy/eggs,
    wild foraging, infant food) and routes it to **mandatory food-safety review (medium risk)**.
  - Requires authoritative references (e.g. USDA/NCHFP) + the **"not a substitute for tested guidance"**
    disclaimer; specifies the per-region authority question as open.
  - Health/medicinal claims policy: strip, or retain only as **documented cultural belief** marked
    non-advice.
- **heritage-recipes-open-ci-001**
  - CI fails on any recipe missing a consent record, attribution block, provenance link, or allergen
    field.
  - CI rejects any recipe whose source is not `approved`, and any `restricted` recipe in the publish set.
  - CI blocks any safety-critical recipe lacking food-safety sign-off and any translation lacking review.

**M0 Definition of Done:** heritage schema v0 published; consent/license/provenance record format
(incl. FPIC + restricted) merged; safety + allergen + non-advice policies merged; right-to-withdraw &
TK-Label design specified; persistent-ID scheme committed; CI consent/attribution/provenance/allergen +
schema gates live; community/steward outreach initiated with status logged; **a qualified
consent/licensing reviewer named (hard exit; if the seat is empty M0 cannot exit — escalate per the
documented fallback in PLAN.md)**. `pnpm build && pnpm test && pnpm lint` green.

---

## Milestone M1 — First consented slice

| ID | Title | Type | Size | Risk | Deliverable | Depends on | Reviewer |
| --- | --- | --- | --- | --- | --- | --- | --- |
| heritage-recipes-open-capture-001 | Build assistive recipe-capture/structuring tool (flag-on-doubt) | code | medium | low | pr | heritage-recipes-open-ci-001 | Maintainer |
| heritage-recipes-open-data-001 | Capture ≥10 recipes from one consented community into valid records | data | large | low | dataset | heritage-recipes-open-capture-001, heritage-recipes-open-partner-001 | Cultural-fidelity reviewer |
| heritage-recipes-open-safety-002 | Food-safety review + allergen tagging for the M1 batch | research | small | medium | document | heritage-recipes-open-data-001 | Food-safety reviewer |
| heritage-recipes-open-qa-001 | Fidelity audit of M1 batch (stratified ≥95%, back-to-source) | research | small | low | document | heritage-recipes-open-data-001 | Cultural-fidelity reviewer |
| heritage-recipes-open-export-001 | JSON-LD + Cooklang/ORF export tooling | code | medium | low | pr | heritage-recipes-open-data-001 | Maintainer |
| heritage-recipes-open-withdraw-002 | Implement + test right-to-withdraw (removal + tombstone + notice) | code | small | low | pr | heritage-recipes-open-export-001, heritage-recipes-open-withdraw-001 | Consent/licensing reviewer |
| heritage-recipes-open-partner-002 | Engage ≥1 candidate community steward for adoption | research | small | low | document | heritage-recipes-open-partner-001 | Maintainer |

**Acceptance criteria (key M1 tasks)**

- **heritage-recipes-open-capture-001**
  - Capture is **assistive**: ambiguous quantities, unfamiliar ingredients, or unclear techniques are
    **flagged for human/tradition-bearer confirmation, never guessed**.
  - Preserves **original names and language**; normalizes quantities to metric while retaining
    customary/original units; gaps remain gaps.
  - Cannot output a publishable record missing consent/attribution/provenance/allergen (mirrors CI).
- **heritage-recipes-open-data-001**
  - ≥10 recipes from one community captured; **100%** carry a valid consent record + attribution +
    provenance + allergen field and pass CI.
  - Variants recorded as co-equal linked records; no "authenticity" ranking.
  - Restricted recipes (if any surfaced) recorded and **excluded** from publication.
  - Conflicting/variant source statements retained with separate provenance.
- **heritage-recipes-open-safety-002**
  - Every safety-critical recipe in the batch reviewed (100%) with authoritative references + disclaimer.
  - Allergen tags populated for all recipes (explicit "unknown" where genuinely unknown).
  - Any health/medicinal claims stripped or marked documented-belief (non-advice).
- **heritage-recipes-open-qa-001**
  - **Stratified** sample (≥50 or whole batch; strata by community & contribution method) verified
    faithful; ≥95% pass; **auditor independent** of the contributor/transcriber.
  - For directly-contributed recipes, a **back-to-source check**: the tradition-bearer confirms fair
    representation.
- **heritage-recipes-open-withdraw-002**
  - A test withdrawal removes the recipe from all project surfaces/exports, emits a tombstone, and
    publishes a downstream-propagation notice within the SLA.
  - Contributor PII tied to the recipe is removed from project-controlled surfaces.

**M1 entry precondition (hard gate):** a consent path for the M1 community is recorded as `approved`
before any capture — signed individual consents, or an **FPIC record** from a verified community
authority for community-level knowledge.

**M1 Definition of Done:** end-to-end pipeline proven on one community's ≥10 recipes; 100% consent +
attribution + provenance + allergen; safety/translation items reviewed at 100%; fidelity audit ≥95%
with back-to-source; JSON-LD + one interop export produced; right-to-withdraw exercised successfully;
≥1 candidate steward in conversation.

---

## Milestone M2 — Usable surface (explorer, exports, reuse)

| ID | Title | Type | Size | Risk | Deliverable | Depends on | Reviewer |
| --- | --- | --- | --- | --- | --- | --- | --- |
| heritage-recipes-open-explorer-001 | Public explorer (no accounts/PII) showing attribution/consent/provenance/allergens/safety | code | medium | low | pr | heritage-recipes-open-export-001 | Maintainer |
| heritage-recipes-open-recon-001 | Ingredient/place reconciliation to Wikidata (assistive, human-confirmed) | data | medium | low | dataset | heritage-recipes-open-data-001 | Cultural-fidelity reviewer |
| heritage-recipes-open-export-002 | Add ORF + CSV exports with full attribution/license metadata | code | small | low | pr | heritage-recipes-open-export-001 | Maintainer |
| heritage-recipes-open-docs-001 | Data dictionary + attribution/citation/reuse guide for consumers | writing | small | low | document | heritage-recipes-open-explorer-001 | Maintainer |
| heritage-recipes-open-metrics-001 | Reuse metrics + contributor-satisfaction check-in mechanism | maintenance | small | low | document | heritage-recipes-open-explorer-001 | Maintainer |

**Acceptance criteria (key M2 tasks)**

- **heritage-recipes-open-explorer-001**
  - Browse a recipe and see its attribution, consent status, provenance, allergens, safety notes +
    disclaimer, and any TK Labels; links to raw exports.
  - Static/no-account; collects no visitor PII; restricted recipes never appear.
- **heritage-recipes-open-metrics-001**
  - Tracks downloads/exports/downstream integrations from M2 onward.
  - Implements a post-publication **tradition-bearer satisfaction** check-in ("represented fairly?")
    and logs results.

**M2 Definition of Done:** explorer live (no accounts/PII, restricted-safe); JSON-LD + Cooklang + ORF +
CSV exports with attribution/license metadata; Wikidata reconciliation (human-confirmed); reuse metrics
+ satisfaction check-in live.

---

## Milestone M3 — Scale, multi-community & steward adoption (shipped)

| ID | Title | Type | Size | Risk | Deliverable | Depends on | Reviewer |
| --- | --- | --- | --- | --- | --- | --- | --- |
| heritage-recipes-open-data-002 | Scale to ≥5 communities / ≥100 recipes with complete records | data | large | low | dataset | heritage-recipes-open-recon-001, heritage-recipes-open-safety-002 | Cultural-fidelity + consent reviewers |
| heritage-recipes-open-i18n-001 | Translate a recipe subset with fluent-reviewer fidelity check | translation | medium | medium | translation | heritage-recipes-open-data-002 | Translation reviewer |
| heritage-recipes-open-partner-003 | Secure steward adoption/co-governance + ≥1 documented citation/use | research | medium | low | document | heritage-recipes-open-partner-002 | Maintainer |
| heritage-recipes-open-sustain-001 | Sustainability, hosting + reviewer-rotation/throughput + withdrawal-SLA plan | writing | small | low | document | heritage-recipes-open-partner-003 | Maintainer |

**Acceptance criteria (key M3 tasks)**

- **heritage-recipes-open-data-002**
  - ≥5 communities and ≥100 recipes published; **100%** consent + attribution + provenance + allergen
    maintained.
  - Each community has a verified consent/FPIC path before its recipes are captured.
  - A fresh stratified fidelity audit still ≥95%; safety-critical recipes reviewed at 100%.
- **heritage-recipes-open-i18n-001**
  - Original-language text retained; each translation credited to its translator.
  - Every translation passes fluent-reviewer fidelity review (100% reviewed; ≥95% accepted).
- **heritage-recipes-open-partner-003**
  - A named community/cultural steward commits to adopt/co-govern, host, and cite the dataset.
  - ≥1 concrete citation or downstream use is documented; community affirms fair representation.

**M3 Definition of Done (project "shipped"):** ≥5 communities / ≥100 recipes with 100% consent +
attribution + provenance + allergen; safety/translation reviewed at 100%; ≥1 steward has
adopted/co-governs and cited the dataset; tradition-bearer satisfaction ≥90%; withdrawal SLA met in
production; sustainability/reviewer-rotation plan in effect.

---

## Backlog / future (sized, unscheduled)

| ID | Title | Type | Size | Risk | Deliverable | Notes |
| --- | --- | --- | --- | --- | --- | --- |
| heritage-recipes-open-data-003 | Ingest a public-domain community cookbook (verified PD edition) | data | medium | low | dataset | Verify edition is PD; facts only; no protected photos |
| heritage-recipes-open-media-001 | Contributor photo/audio intake with independent license records | data | medium | low | dataset | Media licensed separately from text |
| heritage-recipes-open-tk-001 | Operationalize TK Labels in JSON-LD exports + explorer UI | code | medium | low | pr | Local Contexts integration |
| heritage-recipes-open-units-001 | Locale-aware unit/measure normalization library | code | small | low | pr | Metric + customary; preserves originals |
| heritage-recipes-open-quality-001 | Automated anomaly/missing-field flagging for review | code | medium | low | pr | Assistive QA, human-confirmed |
| heritage-recipes-open-i18n-002 | Multilingual ingredient/place labels via Wikidata (CC0) | data | small | low | dataset | CC0 labels only |
| heritage-recipes-open-sparql-001 | Optional hosted query endpoint over the corpus | code | large | low | pr | Depends on steward hosting |
| heritage-recipes-open-withdraw-003 | Downstream-mirror withdrawal-feed subscription format | design-spec | small | low | document | Propagation mechanism for mirrors |

---

## Example task JSON

Schema-valid Task JSON for the first M0 task (`heritage-recipes-open-schema-001`):

```json
{
  "id": "heritage-recipes-open-schema-001",
  "title": "Define heritage Recipe schema (schema.org/Recipe extension + JSON Schema + SHACL)",
  "project": "heritage-recipes-open",
  "type": "design-spec",
  "lane": "donated",
  "priority": "high",
  "domain": ["culture-heritage", "open-data", "food", "education"],
  "riskTier": "low",
  "urgent": false,
  "deliverable": "document",
  "tokenEstimate": "medium",
  "status": "open",
  "context": "An open, consent-first dataset of traditional/regional recipes needs a shared schema before any recipe is captured. Every published recipe must carry a consent record, cultural attribution, source provenance, and an allergen field. Sources are direct consented contributions, public-domain, or openly-licensed only; scraping for-profit sites or copying in-copyright cookbook text/photos is out of scope. Restricted/sacred knowledge is recorded but never published. See PLAN.md.",
  "objective": "Define the heritage Recipe record as a documented extension of schema.org/Recipe, published as JSON Schema + SHACL + a human-readable spec, with round-trippable Cooklang and Open Recipe Format mappings, and the countable consent/attribution/provenance/allergen units the CI gates measure.",
  "acceptanceCriteria": [
    "Recipe record defined as a schema.org/Recipe extension; published as JSON Schema + SHACL + human-readable spec.",
    "Exactly one consent record, one attribution block, one provenance link, and one allergen field are required per published recipe (the countable CI units).",
    "Ingredients/quantities modeled with metric + customary units and original names retained; structured steps; original-language title + translations.",
    "Safety flags, TK-Label slots, and media with an independent license slot are modeled.",
    "Regional/family variants modeled as co-equal linked records (no single 'authentic' winner).",
    "Round-trip mappings to Cooklang and Open Recipe Format documented, with lossy fields noted.",
    "A 'restricted' (recorded-but-never-published) status is representable in the schema."
  ],
  "resources": [
    "planning/projects/heritage-recipes-open/PLAN.md",
    "https://schema.org/Recipe",
    "https://cooklang.org/",
    "https://localcontexts.org/labels/traditional-knowledge-labels/"
  ],
  "output": "A schema specification document (schema/README.md) plus JSON Schema + SHACL artifacts defining the heritage Recipe record, its schema.org/Recipe mapping, and Cooklang/ORF export mappings, committed via PR.",
  "requestor": "jdev1977",
  "verifiedNeed": false,
  "outputLicense": "CC-BY-4.0"
}
```
