# Senior Assist — Project Dashboard

## Architecture

```mermaid
graph TD
    UI[Chrome Extension UI\nSelection overlay + answer panel]
    KB[Knowledge Base\nVersioned YAML/JSON\n135 entries V1]
    OCR[Tesseract.js WASM\nOCR for text-only path]
    LLM_S[Qwen3.5-1.7B Q4\nText model - low RAM]
    LLM_L[Qwen3.5-4B Q4\nVision model - high RAM]
    RUNTIME[WebLLM / llama.cpp WASM\nLocal inference runtime]
    SEARCH[Web Search\nWhitelisted sources - opt-in]

    UI -->|screenshot| OCR
    UI -->|screenshot| LLM_L
    OCR -->|text| LLM_S
    LLM_S --> RUNTIME
    LLM_L --> RUNTIME
    RUNTIME -->|KB lookup first| KB
    RUNTIME -->|fallback| SEARCH
    KB --> UI
    RUNTIME --> UI
    SEARCH --> UI
```

*Updated when architecture changes. Not on every edit.*

## Plan Progress

```mermaid
graph LR
    P1[Phase 1\nExtension scaffold]:::pending
    P2[Phase 2\nRuntime integration]:::pending
    P3[Phase 3\nKB + fallback chain]:::pending
    P4[Phase 4\nSenior UX polish]:::pending
    P5[Phase 5\nV1 KB content\n135 entries]:::pending
    P6[Phase 6\nContribution pipeline]:::pending

    P1 --> P2 --> P3 --> P4 --> P5 --> P6

    classDef done fill:#4ade80,color:#000
    classDef active fill:#facc15,color:#000
    classDef pending fill:#94a3b8,color:#000
```

*Mirrors current implementation plan. Updated as phases complete.*

## Session Log

| Date | Summary | Next |
|------|---------|------|
| 2026-03-06 | Brainstorm: pivoted from Android launcher → fraud prevention → tech literacy Chrome extension. Design approved. | Write implementation plan |

## Where I Left Off

Design doc approved. Project scaffolded at `~/src/senior-assist`. Next: implementation plan via writing-plans skill.
