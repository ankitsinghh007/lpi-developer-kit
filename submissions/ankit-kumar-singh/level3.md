# Level 3 Submission — Ankit Kumar Singh

**Track:** A — Agent Builders  
**GitHub:** [ankitsinghh007](https://github.com/ankitsinghh007)

---

## Agent Repository

**https://github.com/ankitsinghh007/smile-hospital-agent**

---

## What I built

**SMILE Digital Twin Advisor — Hospital Operations**

A domain-specific AI agent that takes a real hospital operations problem and
produces a structured, phase-by-phase SMILE implementation roadmap.

Real-world problems solved:
- Bed utilisation variance (surgical ward at 98%, medical at 60%)
- MRI/CT equipment downtime (10h/week unplanned loss)
- Hospital energy waste (HVAC fixed schedules, 38% cost rise)
- Patient readmission prevention (chronic disease monitoring)

---

## LPI Tools Used (all 7)

| Step | Tool | Why |
|------|------|-----|
| 1 | `smile_overview` | SMILE methodology baseline — always first |
| 2 | `list_topics` | Discover all KB topic areas before searching |
| 3 | `query_knowledge` | Title-boosted first search |
| 4 | `query_knowledge` | Refined second search based on step 3 findings |
| 5 | `get_case_studies` | Domain-matched case evidence |
| 6 | `get_insights` | Scenario-specific SMILE recommendations |
| 7 | `smile_phase_detail` | Deep dive into most relevant phase for domain |
| 8 | `get_methodology_step` | Phase 2 MVT steps — always relevant |

---

## Easter Eggs Found (all 3)

| Egg | Location | Insight |
|-----|----------|--------|
| 🥚 #1 | `src/index.ts` (top comment) | Hidden hint pointing to impact-first search strategy |
| 🥚 #2 | Query `"impact first data last"` | **6 ontology-related entries found** |
| 🥚 #3 | `knowledge-base.json` (`kb-egg`) | Reveals title-weighted scoring → exploited via `_title_boost_query()` |

Full working and code in `HOW_I_DID_IT.md` and `agent.py`.

---

## Key differentiators

1. **Multi-step reasoning loop** — `query_knowledge` called twice: first with
   title-boosted query, second with terms extracted from the first result
2. **Decision routing** — which SMILE phase to deep-dive depends on the domain
   detected from the problem (not hardcoded)
3. **All 7 tools used** — including `list_topics` before searching and
   both `smile_phase_detail` + `get_methodology_step`
4. **Structured output** — Impact Statement → Phase 1 → Phase 2 → Phase 3 →
   Roadmap → Pitfalls → Sources (not prose blob)
5. **Full provenance table** — every tool call shows: tool, why called, chars
   returned, latency

---

## How it works (high-level)

The agent follows a structured pipeline:

1. Detects the problem domain (beds, equipment, energy, or patient outcomes)
2. Discovers available knowledge areas using `list_topics`
3. Performs a title-optimized search using `query_knowledge`
4. Refines the query using signals extracted from initial results
5. Collects supporting evidence from case studies and insights
6. Selects the most relevant SMILE phase dynamically
7. Generates a structured implementation roadmap using an LLM
