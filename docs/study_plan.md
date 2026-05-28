## Changelog
- **v0 --- 11/05/2026** Initial headline claim and research questions.
- **v1 --- 18/05/2026** Pivoting from 2 RQ's into focusing on simulating humans, for now focusing on bias in simulated humans.
- **v2 --- 20/05/2026** Corpus locked to recipe database. Changing RQ2 to better reflect familiarity with certain cuisines rather than expertise (hard to get expert chefs for that comparison)
- **v3 --- 21/05/2026** Dropped the cuisine-familiarity RQ — weak familiarity margin on recipes. Match-only study: two RQs. One fixed seed schema.
- **v4 --- 28/05/2026** Dropped Don't Know Yet (resolved in study_design v2). Added Out of Scope.

---

## Headline Claim
Simulated humans diverge from real human users during conversational schema creation in measurable and predictable ways. This project maps the divergence axes — testing where simulated users differ from human users.

## Core Premise
Simulated users are cheap and scalable and are being used more and more often in development. We want to quantify the failures that these models face.

## Research Questions

### RQ1: On which edit types do sim-users diverge most from humans?
- **Hypothesis:** Divergence happens mostly on merge and delete — sim-users over-merge and under-delete relative to humans.
- **Null:** Divergence rate is uniform across edit types.

### RQ2: Do sim-users converge faster and to more-merged schemas than humans?
- **Hypothesis:** Sim-users finish in fewer turns and more merging.
- **Null:** Sim-user session length and terminal schema size fall within human range.

See `study_design.md` v2 for measures, sample size, and decision rule.

## Out of Scope
- **Expertise / familiarity gradient.** Dropped at v3 — recipe corpus does not produce a strong enough expertise margin between participants.
- **Extraction backbone swap.** Backbone held constant; whether divergence is backbone-specific vs LLM-general is not under study.
