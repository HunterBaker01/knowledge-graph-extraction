## Changelog
- **V0 --- 2026-05-20** Initial study design. Recipe corpus, within-subject cuisine-familiarity design, single-session.
- **V1 --- 2026-05-21** Dropped RQ2 and the cuisine-familiarity axis — weak familiarity margin on recipes. Match-only study: RQ1 + RQ3. One fixed seed schema.
- **V2 --- 2026-05-27** Locked measures and statistical tests for RQ1 and RQ2. Named primary outcomes per RQ. Added pre-registered decision rule. Locked initial seed-schema content, subject to revision after pilot. Added bootstrap power calculation to sample-size justification.

---

## Conditions

- Every session starts from one fixed, deliberately messy seed schema
  built from a fixed recipe sample. Identical for every agent.
- The only manipulated factor is agent type (human or sim-user).
- Human sessions are the baseline condition. Sim-user sessions are
  the treatment condition. The headline claim is evaluated by comparing the
  sim-user population to the human baseline on each primary outcome.
- All agents perform the same task: edit the seed schema via the assistant-proposal turn
  loop until they mark it Done.

---

## Variables

**Manipulated.**

- Agent type.

**Observed (dependent).**

- Per-edit-type counts and frequencies — add / merge / split / rename / delete.
- Edit source — assistant-proposed vs user-initiated
- Terminal schema node count.
- Turn count per session.
- Logged per edit event: turn index, action type, edit source, proposal disposition, target node/edge, timestamp.

**Held constant.**

- Sim-user LLM: `claude-opus-4-7`, fixed decoding parameters.
- Seed schema — one fixed seed schema, identical for every session.
- Recipe corpus sample.
- Assistant / extraction backbone.
- Turn cap: 30 assistant-proposal turns per session. Session auto-terminates if reached; otherwise terminates when the user marks Done.

---

## Corpus

**Source.** TheMealDB recipe dataset — each recipe has a name, cuisine, category, tags,
ingredients (name + measure), and instructions.

**Seed schema sample.** One fixed sample of recipes spanning several cuisines, chosen for
a rich graph. The same sample seeds the single combined schema used in every session.

**Recipes (8 dishes, 3 cuisines).**

| id    | name                        | cuisine | category   |
|-------|-----------------------------|---------|------------|
| 53064 | Fettuccine Alfredo          | Italian | Pasta      |
| 52835 | Fettucine alfredo           | Italian | Pasta      |
| 52839 | Chilli prawn linguine       | Italian | Pasta      |
| 52826 | Braised Beef Chilli         | Mexican | Beef       |
| 52870 | Chickpea Fajitas            | Mexican | Vegetarian |
| 53366 | Beef and Broccoli Stir-Fry  | Chinese | Beef       |
| 52952 | Beef Lo Mein                | Chinese | Beef       |
| 53367 | Chicken Fried Rice          | Chinese | Chicken    |

**Schema structure.** Nodes: `Dish`, `Cuisine`, `Category`, `Ingredient`.
Edges: `dish->cuisine`, `dish->category`, `dish->ingredient`.

- *Duplicate nodes (5).* `Tomato` / `Tomatoes`; `Olive Oil` / `Oil`;
  `Chilli` / `Chili`; `Soy Sauce` / `Soy`; the two Fettuccine dishes left
  as separate `Dish` nodes.
- *Wrong merges (3).* `Onion + Garlic` collapsed into one node;
  `Cumin + Paprika` collapsed; `Beef + Chicken` collapsed under `Meat`.
- *Over-splits (3).* `Egg Yolk` + `Egg White` as two nodes instead of one
  `Egg`; `Black Pepper` + `White Pepper` + `Pepper` as three nodes;
  `Chicken Breast` + `Chicken Thigh` as two nodes instead of one `Chicken`.

---

## Procedure

**Single session per participant.**

1. **Onboarding.** Consent and intro, short UI tutorial.
2. **Edit session.**
   - Starts from the fixed pre-seeded schema — messy by design (duplicate nodes,
     wrong merges, over-splits) for dense edit opportunity.
   - Turn loop: the assistant proposes one edit (add / merge / split / rename / delete on
     a node or edge) the user accepts, rejects, or counter-edits.
   - The user works until they mark the schema **Done**.
3. **Wrap.** Terminal schema saved.

**Assistant.** Held constant — a fixed LLM (`claude-opus-4-7`) with a versioned prompt,
proposing edits from the current schema state and recipe sample. Same assistant for every
human and sim session.

**Sim session.** Identical schema, assistant, and proposal loop. The sim-user LLM plays
the user role. The sim runs the same turn loop and signals Done itself.

---

## Sample Size

**Humans.** Target N = 20.

**Sim-users.** 120 sessions on the fixed seed schema.

**Justification.** Human N is bounded by recruiting capacity. Power was assessed
by simulation rather than chosen.

Bootstrap power calculation: two normal populations with Cliff's $\delta$ as the
target effect size, $n_\text{human} = 20$, $n_\text{sim} = 120$, $\alpha = 0.05$,
Mann-Whitney $U$, 10,000 iterations.

| target $\delta$ | two-sided power | one-sided power |
|---|---|---|
| 0.28 | 0.51 | --- |
| **0.33** (Romano "medium") | **0.67** | **0.78** |
| 0.43 (Romano "large") | 0.90 | --- |
| 0.50 | 0.96 | --- |

Decision rule uses directional comparisons with pre-registered sign on each
primary outcome, so the one-sided column applies. Power at the decision-rule
threshold $\delta = 0.33$ is 0.78 --- below the 0.80 convention by a small
margin.

---

## Primary Outcome

**RQ1.** Per-session proportion of `merge` edits and per-session proportion of
`delete` edits, compared sim vs human population (Cliff's $\delta$ with
Holm-corrected Mann-Whitney $U$). Pre-registered as the two primary outcomes
for RQ1. Proportions for `add`, `split`, and `rename` are secondary, but not the hypothesis-supporting test.

**RQ2.** Per-session turn count and per-session merge ratio, compared sim vs
human population (Cliff's $\delta$ with Mann-Whitney $U$). Pre-registered as
the two primary outcomes for RQ2. Terminal node count is secondary.

---

## Decision Rule

Pre-registered. Maps test output to verdict before data collected.

Effect-size threshold: $|\delta| \geq 0.33$ (Romano "medium"). Avoids
significant-but-trivial results at the 120-session sim sample size.

### RQ1 --- directional (sim over-merges, sim under-deletes)

Hypothesis supported iff both hold:

- `merge`: Holm-corrected $p < 0.05$, $\delta > 0$, $|\delta| \geq 0.33$.
- `delete`: Holm-corrected $p < 0.05$, $\delta < 0$, $|\delta| \geq 0.33$.

### RQ2 --- directional (sim fewer turns, sim higher merge ratio)

Hypothesis supported iff both hold:

- `turn_count`: $p < 0.05$, sim median $<$ human median, $|\delta| \geq 0.33$.
- `merge_ratio`: $p < 0.05$, sim median $>$ human median, $|\delta| \geq 0.33$.

---

## Measures

All tests are non-parametric. Bootstrap 95\% CIs throughout.

### RQ1 --- edit-type divergence

**Per-session unit.** Edit-type frequency vector over the five categories
(add, merge, split, rename, delete)
Counts normalized to proportions per session.

**Per-type test.** Mann-Whitney U on each of the five components,
sim-population vs human-population. Holm-Bonferroni correction across the five
tests at family-wise $\alpha = 0.05$.

**Per-type effect size.** Cliff's $\delta$ with bootstrap 95\% CI. Sign indicates
direction of divergence (positive $\delta$ = sim higher than human on that edit type).

### RQ2 --- convergence speed and terminal schema shape

Three per-session scalars, pre-registered as separate hypotheses. No multiple-test correction across them; all reported regardless of significance.

1. **Turn count.** Total assistant-proposal turns until session marked Done (or cap reached).
2. **Terminal node count.** $|V|$ of final schema.
3. **Merge ratio.** $1 - |V_\text{terminal}| / |V_\text{seed}|$. Direct readout
   of the over-merge hypothesis.

**Test.** Mann-Whitney $U$ sim vs human on each scalar. Cliff's $\delta$ with
bootstrap 95\% CI. Report sim median, human median, $\delta$, and CI per scalar.

---

## Notes

- Multiple sim-user models — adds an "is divergence model-specific?" angle. Deferred; single model held constant for V0.
