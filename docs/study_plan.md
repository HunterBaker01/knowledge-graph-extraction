## Changelog
- **V0 --- 11/05/2026** Initial headline claim and research questions.

---

## Headline Claim
Two cheap proxies that conversational graph extraction research depends on — Seo et al.'s structural metrics for schema quality, and LLM-simulated users for development feedback — only track ground-truth utility within narrow conditions. This project maps where they hold and where they break.

## Core Premise
Are schemas defined upfront better or worse than schemas learned through conversation with the data?

## Research Questions

### Do Seo et al's 6 structural metrics actually tell us a knowledge graph is good?
- **Hypothesis:** A linear combination of the 6 metrics beats the best single metric.
- **Null:** Metrics measure shape, not utility. So cross-domain usage is not good.

### Can LLM-simulated user feedback substitute for human feedback?
- **Hypothesis:** Final schemas reached with simulated users fall within the human inter-rater envelope on Seo metrics.
- **Null:** Simulated user systematically over-merges or under-prunes, detectable bias beyond CI.

## Don't Know Yet
- What counts as the "same domain" for two corpora?
- How to give simulated user and human the same access to corpus? Do sim user may have hidden background knowledge?
- How to compare Seo metric scores against gold ontology when no gold ontology exists for the chosen corpora?
- What size corpus is big enough?
