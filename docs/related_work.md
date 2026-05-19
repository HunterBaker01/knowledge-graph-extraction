## Changelog
- **V0 --- 11/05/2026** Initial related work
- **V1 --- 19/05/2026** Restructured around sim-human bias-map focus. Taking out the SEO focus.

---

## Core: Simulated Users

**Park et al. (2023) — Generative Agents: Interactive Simulacra of Human Behavior.** [arXiv:2304.03442](https://arxiv.org/abs/2304.03442). Paper for LLM agents simulating individual human behavior over long periods.

**Park et al. (2024) — Generative Agent Simulations of 1,000 People.** [arXiv:2411.10109](https://arxiv.org/abs/2411.10109). Replication study: 1,000 LLM agents conditioned on interview data to mimic specific humans.

**Argyle et al. (2023) — Out of One, Many: Using Language Models to Simulate Human Samples.** [arXiv:2209.06899](https://arxiv.org/abs/2209.06899). LLMs conditioned on demographics reproduce opinion distributions. Directly motivates population-match framing and exposes the persona-conditioning question (RQ2).

**Aher, Arriaga, Kalai (2023) — Using Large Language Models to Simulate Multiple Humans and Replicate Human Subject Studies.** [arXiv:2208.10264](https://arxiv.org/abs/2208.10264). Paper on using sim-users as experimental subjects.

**Horton (2023) — Large Language Models as Simulated Economic Agents: What Can We Learn from Homo Silicus?** [arXiv:2301.07543](https://arxiv.org/abs/2301.07543). Behavioral simulation. Useful framing for our edit-decision-as-behavior view.

**Santurkar et al. (2023) — Whose Opinions Do Language Models Reflect?** [arXiv:2303.17548](https://arxiv.org/abs/2303.17548). Shows LLMs' opinion distributions skew demographically. Directly relevant to bias direction in RQ1 and the prior-knowledge-leak hypothesis.

**"LLM-Simulated Users are Unreliable Proxies for Human..." (2026).** [arXiv:2601.17087](https://arxiv.org/abs/2601.17087). Most direct precedent that argues do systematically diverge from human users. Close neighbor to our headline claim.

---

## Conversational Graph Construction

**Pan et al. (2025) — LLMs4SchemaDiscovery / SCHEMA-MINER.** [arXiv:2504.00752](https://arxiv.org/abs/2504.00752). Human-in-the-loop schema mining with iterative LLM + expert feedback in materials science. The "expert" loop is the human role we then swap with a sim-user.

**Kommineni, König-Ries, Samuel (2024) — From human experts to machines: An LLM supported approach to ontology and knowledge graph construction.** [arXiv:2403.08345](https://arxiv.org/abs/2403.08345). Uses LLM-as-judge for evaluation. Precedent for swapping a human evaluator with an LLM.

---

## Background: Extraction Backbone

**Zhang & Soh (2024) — Extract-Define-Canonicalize (EDC).** [arXiv:2404.03868](https://arxiv.org/abs/2404.03868). Three-phase LLM pipeline for KG construction. Reusable as our extraction backend so sessions have something to react to. Not under study.
