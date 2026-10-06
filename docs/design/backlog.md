# Backlog

> Initial task list, derived from the [system design](system-design.md). Items will be added, merged, or reprioritized as the project evolves.

## Priorities

| Label | Meaning |
|---|---|
| **P0** | MVP, must have |
| **P1** | Next, after MVP core works |
| **P2** | Later |

## Overview

| ID | Task | Area | Priority |
|---|---|---|---|
| T1 | Chat system prompt and output schema | AI | P0 |
| T2 | Test LLM models on 10 Libyan-dialect examples | AI, Dialect | P0 |
| T3 | Rule-based risk detection and static emergency screen | Safety | P0 |
| T4 | Four-level escalation flow | Safety | P0 |
| T5 | Decision engine for final risk level | Safety | P0 |
| T6 | History-based risk scoring | Safety | P0 |
| T7 | Output filter (layers 1-3) | Safety | P0 |
| T8 | Pre-written safe fallback replies | Safety | P0 |
| T9 | Libyan dialect risk and distress lexicon | Dialect, Safety | P0 |
| T10 | Verified local resource directory | Content | P0 |
| T11 | Encrypted local storage and PII masking | Privacy | P0 |
| T12 | First-use notice and age policy | Privacy, Product | P0 |
| T13 | Flutter project skeleton | App | P0 |
| T14 | Verify Libyan emergency numbers | Safety, Content | P0 |
| T15 | Recruit mental health specialist reviewer | Team | P0 |
| T16 | Pre-reviewed exercises library | Content | P1 |
| T17 | Mood and topic tracking | App | P1 |
| T18 | Arabizi and text normalization | Dialect | P1 |
| T19 | Expand dialect evaluation set to 200+ | Dialect | P1 |
| T20 | Red-team test set | Safety | P1 |
| T21 | Resource matching with embeddings and RAG | AI | P2 |
| T22 | Weekly mood indicators | App | P2 |
| T23 | LLM-as-judge filter for levels 1-2 | Safety | P2 |
| T24 | Repo structure: separate .github repo and visibility | Repo | P2 |

---

## P0: MVP

### T1. Chat system prompt and output schema

Supportive chat in Libyan dialect, empathetic, no diagnosis.

- [ ] Prompt forbids diagnosis, medication, and dosage
- [ ] Model acts as an objective facilitator, gently challenging assumptions (no people-pleasing)
- [ ] Libyan dialect style guide with few-shot examples
- [ ] JSON output: `reply`, `risk_level` (0-3), `signals`, `mood`, `topics`, `confidence`, `suggested_action`
- [ ] Documented in `docs/`

### T2. Test LLM models on 10 Libyan-dialect examples

- [ ] Write 10 realistic dialect messages covering levels 0-3
- [ ] Compare candidate models on dialect understanding, empathy, classification accuracy, safety
- [ ] Record results and choose a provider

Depends on: T1.

### T3. Rule-based risk detection and static emergency screen

- [ ] Rules run offline, before the model
- [ ] Covers Libyan dialect, MSA, and Arabizi
- [ ] Level 3 shows a static screen with emergency numbers and a trusted person button; the LLM generates nothing
- [ ] Tests for detection

Depends on: T9, T14.

### T4. Four-level escalation flow

| Level | Action |
|---|---|
| 0 Normal | Supportive chat |
| 1 Elevated | Continue chat, check-in question, suggest exercise or resource |
| 2 High | Continue chat, suggest contact with a ready-made message the user sends |
| 3 Imminent | Static emergency screen |

- [ ] Levels 1-2 never end the conversation
- [ ] Nothing is sent without user consent

### T5. Decision engine for final risk level

Deterministic code, not AI.

- [ ] `final_level = max(rule_level, classifier_level, history_level)`
- [ ] Classifier can only raise the level, never lower it below the rules
- [ ] No automatic de-escalation after level 3 within a session
- [ ] Unit tests

### T6. History-based risk scoring

- [ ] Cumulative score over recent messages and days, with time decay, stored locally
- [ ] Moderate signal 3 times in 7 days raises the level by one
- [ ] Tune decay parameters
- [ ] Tests

### T7. Output filter (layers 1-3)

- [ ] Layer 1: JSON schema, allowed actions, length
- [ ] Layer 2: lexicon and regex for means of harm, drugs and dosages, diagnosis phrases, medical promises
- [ ] Layer 3: provider moderation API
- [ ] On failure: show a pre-written safe reply, log locally, no retry

### T8. Pre-written safe fallback replies

- [ ] One or more reviewed replies per level, in dialect
- [ ] Level 3 screen text

Reviewed by: T15.

### T9. Libyan dialect risk and distress lexicon

- [ ] Expressions written and reviewed by Libyans from east, west, and south
- [ ] Arabizi variants
- [ ] Used by the rule detector (T3) and classifier (T1)

### T10. Verified local resource directory

- [ ] Data schema: name, type, city, contact, language, verification date
- [ ] Start with about 20 verified entries (specialists, hotlines, university support)
- [ ] Review and update process

### T11. Encrypted local storage and PII masking

- [ ] Encrypted on-device storage, no account
- [ ] Mask names, numbers, and places before text reaches the model
- [ ] Consent flow for anything sent externally
- [ ] Delete history on request

### T12. First-use notice and age policy

- [ ] Clear message that Manara is not a diagnosis or substitute for professional care
- [ ] Decide age policy (18+, or 13+ with conditions)

### T13. Flutter project skeleton

- [ ] Initialize app and folder structure
- [ ] Linting and CI
- [ ] State management choice
- [ ] Arabic RTL and localization

### T14. Verify Libyan emergency numbers

- [ ] Confirm emergency and mental health hotlines from official sources
- [ ] Record source and verification date

### T15. Recruit mental health specialist reviewer

- [ ] Find a specialist to review the lexicon, exercises, fallback replies, and level 2 responses

---

## P1: Next

### T16. Pre-reviewed exercises library

- [ ] Breathing, grounding, journaling, and similar techniques
- [ ] Model selects from this set; it never invents therapy
- [ ] Clinical review (T15)

### T17. Mood and topic tracking

- [ ] Store mood and topics locally per conversation
- [ ] Feed history-based scoring (T6)

### T18. Arabizi and text normalization

- [ ] Normalize Arabic spelling variants
- [ ] Handle Arabizi before classification

### T19. Expand dialect evaluation set to 200+

- [ ] Grow from the 10-example pilot
- [ ] Libyan reviewers rate naturalness, understanding, classification accuracy

### T20. Red-team test set

- [ ] Risky messages and jailbreak attempts in dialect
- [ ] Run on every prompt change and track pass rate

---

## P2: Later

### T21. Resource matching with embeddings and RAG

Match the user's problem to the directory. Depends on: T10.

### T22. Weekly mood indicators

Show weekly patterns, for example exam stress. Depends on: T17.

### T23. LLM-as-judge filter for levels 1-2

Add only if tests show bad replies passing T7 layers 1-3.

### T24. Repo structure

Org profile files live in this repo, but GitHub needs a repo named `.github` for the org profile. Decide whether to split it out and whether this repo should be private.

---

## Suggested order

1. T1 and T2 (prompt, schema, model test), with T14 and T15 in parallel
2. T9, T3, T5, T7, T8 (safety core)
3. T13, T11, T4, T12 (app shell and privacy)
4. T10, then P1 items
