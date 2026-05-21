## Changelog
- **V0 --- 2026-05-20** Initial study design. Recipe corpus, within-subject cuisine-familiarity design, single-session.
- **V1 --- 2026-05-21** Dropped RQ2 and the cuisine-familiarity axis — weak familiarity margin on recipes. Match-only study: RQ1 + RQ3. One fixed seed schema.

---

## Conditions

- Every session — human and sim — starts from one fixed, deliberately messy seed schema
  built from a fixed recipe sample. Identical for every agent.
- The only manipulated factor is agent type (human vs sim-user), between-subject.
- All agents perform the same task: edit the seed schema via the assistant-proposal turn
  loop until they mark it Done.

---

## Variables

**Manipulated.**
- Agent type — human / sim-user (between-subject). The only manipulated factor.

**Observed (dependent).**
- Per-edit-type counts and frequencies — add / merge / split / rename / delete.
- Edit source — assistant-proposed vs user-initiated
- Terminal schema node count and depth.
- Turn count per session.
- Logged per edit event: turn index, action type, edit source, proposal disposition, target node/edge, timestamp.

**Held constant.**
- Sim-user LLM: `claude-opus-4-7`, fixed decoding parameters.
- Seed schema — one fixed seed schema, identical for every session.
- Recipe corpus sample.
- Assistant / extraction backbone.

---

## Corpus

**Source.** TheMealDB recipe dataset — each recipe has a name, cuisine, category, tags,
ingredients (name + measure), and instructions.

**Seed schema sample.** One fixed sample of recipes spanning several cuisines, chosen for
a rich graph. The same sample seeds the single combined schema used in every session.

---

## Procedure

**Single session per participant.**

1. **Onboarding.** Consent and intro, short UI tutorial.
2. **Edit session.**
   - Starts from the fixed pre-seeded schema — deliberately messy (duplicate nodes,
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

**Justification.** Human N is bounded by recruiting capacity, so sample size is not chosen
to and is what we have to work with.

---

## Measures

RQ measures and statistical tests are not yet finalized, changes will be reflected in changelog.

---

## Notes

- Multiple sim-user models — adds an "is divergence model-specific?" angle. Deferred; single model held constant for V0.
