## Changelog
- **V0 --- 11/05/2026** Initial headline claim and research questions.
- **v1 --- 18/05/2026** Pivoting from 2 RQ's into focusing on simulating humans, for now focusing on bias in simulated humans.
- **v2 --- 20/05/2026** Corpus locked to recipe database. Changing RQ2 to better reflect familiarity with certain cuisisines rather than expertise (hard to get expert chefs for that comparison)

---

## Headline Claim
There is a measurable and predictable way that simulated humans diverge from real human users during conversational schema creation. This project is looking at the mapping the divergence axes, to tests where simulated users differ from human users.

## Core Premise
Simulated users are cheap and scalable and are being used more and more often in development. We want to quantify the failures that these models face.

## Research Questions

### RQ1: On which edit types do sim-users diverge most from humans?
- **Hypothesis:** Divergence happens mostly on merge and delete — sim-users over-merge and under-delete relative to humans.
- **Null:** Divergence rate is uniform across edit types.

### RQ2: Is the persona decorative or do the edits match the familiarity they are claiming to have?
**Hypothesis:** The persona's match more closely with the familiarity they arae trying to simulate rather than each other.
- **Null:** Persona prompt is decorative — sim divergence to humans does not depend on persona-familiarity alignment.

### RQ3: Do sim-users converge faster and to more-merged schemas than humans?
- **Hypothesis:** Sim-users finish in fewer turns and more merging.
- **Null:** Sim-user session length and terminal schema size fall within human range.

## Don't Know Yet
- What size corpus is big enough? How many recipe's from each cuisine?
- Where to start the schema in order for the experiment to run?
- How many questions per session?
- How to measure the difference?
- How to model the experiment?
