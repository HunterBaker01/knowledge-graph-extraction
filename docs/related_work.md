## Changelog
- **V0 --- 11/05/2026** Initial related work.
- **V1 --- 19/05/2026** Restructured around sim-human bias-map focus. Dropped SEO focus.
- **V2 --- 28/05/2026** Realigned with `study_plan.md` v3. RQ2 is now convergence speed fixed stale RQ tags. Added Salecha and Hewitt.

---

## Core: Simulated Users

**Park et al. (2023) — Generative Agents: Interactive Simulacra of Human Behavior.** [arXiv:2304.03442](https://arxiv.org/abs/2304.03442). LLM agents simulating individual human behavior over long horizons — fidelity precedent.

**Park et al. (2024) — Generative Agent Simulations of 1,000 People.** [arXiv:2411.10109](https://arxiv.org/abs/2411.10109). 1,000 LLM agents conditioned on interview data to mimic specific humans — population-fidelity benchmark.

**Argyle et al. (2023) — Out of One, Many: Using Language Models to Simulate Human Samples.** [arXiv:2209.06899](https://arxiv.org/abs/2209.06899). LLMs reproduce opinion distributions — motivates the population-match framing used for sim-vs-human comparison.

**Aher, Arriaga, Kalai (2023) — Using Large Language Models to Simulate Multiple Humans and Replicate Human Subject Studies.** [arXiv:2208.10264](https://arxiv.org/abs/2208.10264). Sim-users as experimental subjects — same substitution this study runs.

**Horton (2023) — Large Language Models as Simulated Economic Agents: What Can We Learn from Homo Silicus?** [arXiv:2301.07543](https://arxiv.org/abs/2301.07543). Behavioral simulation framing — justifies the edit-decision-as-behavior view.

**Santurkar et al. (2023) — Whose Opinions Do Language Models Reflect?** [arXiv:2303.17548](https://arxiv.org/abs/2303.17548). LLM opinion distributions skew in measurable directions — supports the directional-bias prior in RQ1.

**Salecha et al. (2024) — Sycophancy in Persona LLMs.** Sycophancy as a measurable LLM failure mode — predicts the over-merge / under-delete direction in RQ1 and the fewer-turns prediction in RQ2.

**Hewitt et al. (2024) — LLMs as Social-Science Subjects.** Methodology for running LLM subjects under human-subjects protocols — informs the held-constant assistant, seed, and decoding choices.

**"LLM-Simulated Users are Unreliable Proxies for Human Users" (2026).** [arXiv:2601.17087](https://arxiv.org/abs/2601.17087). Closest precedent — argues sim-users systematically diverge from humans in interactive evaluation.

---

## Conversational Graph Construction

**Pan et al. (2025) — LLMs4SchemaDiscovery / SCHEMA-MINER.** [arXiv:2504.00752](https://arxiv.org/abs/2504.00752). Human-in-the-loop schema mining with iterative LLM + expert feedback — the expert loop this study swaps with a sim-user.

**Kommineni, König-Ries, Samuel (2024) — From human experts to machines: An LLM supported approach to ontology and knowledge graph construction.** [arXiv:2403.08345](https://arxiv.org/abs/2403.08345). LLM-as-judge precedent — same human-to-LLM substitution, on the judge side rather than the user side.

---

## Background: Extraction Backbone

**Zhang & Soh (2024) — Extract-Define-Canonicalize (EDC).** [arXiv:2404.03868](https://arxiv.org/abs/2404.03868). Three-phase LLM pipeline for KG construction — reused as the extraction backend so sessions have a real schema to react to. Held constant; not under study.
