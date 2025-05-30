# 🧪 Open Deep Research — LangGraph Unrolled  
*A hands-on walkthrough & refactor of the original [langchain-ai/open_deep_research](https://github.com/langchain-ai/open_deep_research) demo.*

---

## What we built

| Stage | We… | Why it matters |
|-------|-----|----------------|
|⚙️ **State Design**|Declared `ReportState`, `SectionState`, helpers & typed outputs.|Makes every step deterministic and checkpoint-friendly.|
|🛠 **Utility Layer**|Wrapped **Tavily**, **Perplexity**, **Exa**, **arXiv** & **PubMed** search APIs + text formatters.|Modular search back-ends without touching core graph logic.|
|🧩 **Nine Graph Nodes**|• `generate_report_plan` • `human_feedback` • `generate_queries` • `search_web` • `write_section` • `write_final_sections` • `gather_completed_sections` • `initiate_final_section_writing` • `compile_final_report`|Each node does **one** thing → easier to debug / swap providers.|
|🔗 **Nested LangGraph**|Embedded a *section-builder* sub-graph inside the outer *report* graph.|Parallel section writing while preserving global state.|
|💾 **Checkpointing**|Plugged `MemorySaver` so we can pause/ resume / swap models mid-run.|Survives rate-limit errors & lets us tweak provider configs on the fly.|
|🎛 **Provider Switching**|Added `alt_cfg` overrides (OpenAI o3 instead of Anthropic) without kernel restart.|Demonstrates production-style fall-back & cost control.|
|📄 **Final Output**|Generated a fully-formatted, source-cited report on **DeepSeek-R1**.|Proves end-to-end flow—from topic prompt to polished report—in ~100 lines of orchestration code.|

---

## Repo layout
open-deep-research/
├─ 01_state.ipynb # Task 1 – State & dataclasses
├─ 02_utils.ipynb # Task 2 – API wrappers & helpers
├─ 03_nodes.ipynb # Tasks 3-9 – all graph nodes
├─ 04_graph.ipynb # Build, checkpoint, resume demo
└─ README.md # ← you are here




