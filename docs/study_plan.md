## Changelog
- **V0 --- 11/05/2026** Initial headline claim and research questions.
- **v1 --- 18/05/2026** Pivoting from 2 RQ's into focusing on simulating humans, for now focusing on bias in simulated humans.

---

## Headline Claim
There is a measurable and predictable way that simulated humans diverge from real human users during conversational schema creation. This project is looking at the mapping the divergence axes, to tests where simulated users differ from human users.

## Core Premise
Simulated users are cheap and scalable and are being used more and more often in development. We want to quantify the failures that these models face.

## Research Questions

### On which edit types do sim-users diverge most from humans?
- **Hypothesis:** Divergence happens mostly on merge and delete — sim-users over-merge and under-delete relative to humans.
- **Null:** Divergence rate is uniform across edit types.

### Is the persona decorative or do the edits match the expertise they are claiming to be?
**Hypothesis:** The persona's match more closely with the expertise they are trying to simulate rather than each other.
- **Null:** Persona prompt is decorative — sim divergence to humans does not depend on persona-expertise alignment.

### Do sim-users converge faster and to more-merged schemas than humans?
- **Hypothesis:** Sim-users finish in fewer turns and more merging.
- **Null:** Sim-user session length and terminal schema size fall within human range.

## Don't Know Yet
- How to give simulated user and human the same access to corpus? Do sim user may have hidden background knowledge?
- What size corpus is big enough?
- How to model the experiment?
