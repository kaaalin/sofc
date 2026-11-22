# SOF Airside passenger assistant prototype

Interactive Terminal 2 passenger assistant based on Kalin Yanev’s Part A presentation and the supplied 50-question CSV.

## Run

Serve `dist/` with any static HTTP server. For example: `python -m http.server 8080 --directory dist`.
Run verification with `node tests.mjs`.

## Implemented

- English / Bulgarian passenger answers and passenger UI.
- All 50 CSV questions, with searchable language-filtered library.
- Curated bilingual knowledge and deterministic intent matching, with supported paraphrases.
- Follow-up flight and gate selection; fictional sample flights and routes.
- Source citations, proposed owners, version metadata and answer traces.
- Operational scenario switches: normal service, overnight fog, expired source.
- Suppression of stale flight / facility answers and journey-card details.
- Simulated human availability, handover summaries and explicit unavailable-team fallback.
- Routing checks with individual results and exports; no accuracy claim.
- Conversation and traces are session-memory only; exports are user-initiated local downloads.

## Important boundaries

This is a front-end behavioral prototype. It does not connect to Azure, SITA, an airport SSOT, live flight feeds, staff queues, a vector index, or an LLM. Exact known questions and intent rules retrieve hand-authored records. Unknown queries fall back rather than generating answers. Simulated availability is not a staffing guarantee. The facilities, gate routes, walking times and flights in the demo are fictional, expressly labelled, and not suitable for passenger navigation. Role-based owners are proposed rather than approved assignments.

Public reference guidance links to the European Commission (liquids), EASA (power banks), and Your Europe (air passenger rights). Airport security / legal approval remains required. No official airport facility details are asserted from conflicting public listings.

Source expiry and urgent notices are scenario fixtures. Source approval, ingestion and real TTL checks require production implementation. No pre-display LLM judge, post-answer LLM judge, accuracy scoring, automatic learning, retraining or live staff delivery is implemented.

The plan's 95% launch target requires independent BG/EN reference-answer evaluation on 500 unseen cases, critical-error review and confirmed operational handovers. The built-in 50 checks validate routing only. Appropriate *completed* handovers may count as correct; suggested or unavailable routes cannot.

Passenger feedback and retraining are reserved for the next phase, following the deck.

## Verification

All 50 CSV exact-input routes plus follow-up, unknown-flight, invalid-gate, source-expiry, disruption override, guardrail, unavailable-team, language and selected paraphrase checks passed. Browser checks verified flight clarification, sample flight selection, Bulgarian replies, 50 routing results, overnight fog override, expired-source blocking and unavailable handover summary.
