# System Design (Draft)

> Initial design. It will change as models are tested and specialists review the approach.

## 1. MVP scope

| Priority | Feature | Reason |
|---|---|---|
| P0 | Supportive chat in Libyan dialect | Core of the app |
| P0 | Two-layer risk detection (fixed rules + LLM classifier) | Safety first |
| P0 | Four-level escalation engine with an offline, static emergency screen | Safety |
| P0 | PII masking, encrypted on-device storage, not-a-diagnosis notice | Privacy and trust |
| P0 | Small verified resource directory (about 20 entries to start) | Guidance is the core value |
| P1 | Pre-reviewed exercises library (breathing, grounding, journaling) | The model selects, never invents |
| P1 | Mood and topic tracking | Feeds history-based risk assessment |
| P2 | RAG resource matching, weekly indicators | Needs a larger directory first |

## 2. Message pipeline

```
User message
   |
   v
[1] On-device preprocessing: mask names, numbers, places
   |
   +--> [2a] Fixed rule detector (instant, offline)
   |         Risk lexicon: Libyan dialect, MSA, Arabizi
   |
   +--> [2b] LLM classifier returns JSON:
   |         risk_level, signals, mood, topics, confidence
   v
[3] History-based assessment
    Cumulative risk score over recent messages and days, with time decay
   |
   v
[4] Decision engine (deterministic code, not AI)
    final_level = max(rule_level, classifier_level, history_level)
   |
   v
[5] Response for that level, then output filter before display
```

### Classifier signals

Suicidal ideation, plan, access to means, timeframe, self-harm, harm to others, exposure to violence or abuse, hopelessness.

### History rules (initial)

- A moderate signal repeated 3 times within 7 days raises the level by one.
- After reaching level 3, the level does not drop automatically within the same session.
- The classifier can only raise the level; it can never lower it below the rule detector.

## 3. Escalation levels

| Level | When | Action |
|---|---|---|
| 0 Normal | Venting, everyday stress | Supportive chat; suggest an exercise when useful |
| 1 Elevated | Recurring distress, mild hopelessness | Continue chat, add a check-in question, suggest an exercise or resource |
| 2 High | Self-harm thoughts without a plan | Continue chat, suggest contacting a specialist or trusted person with a ready-made message the user sends themselves |
| 3 Imminent | Plan, means, or timeframe | Static screen with emergency numbers and a trusted person button. The LLM generates nothing |

Levels 1 and 2 do not end the conversation, to avoid the "helpline fatigue" users reported.

## 4. Libyan dialect

1. **Style guide in the system prompt:** neutral Libyan dialect understood in the east, west, and south, with real few-shot examples.
2. **Dialect lexicon** of distress and risk expressions, written and reviewed by Libyans. Feeds both the rule detector and the classifier.
3. **Arabizi support** (Latin letters and digits) and text normalization before classification.
4. **Evaluation set:** start with 10 examples, grow to 200+. Libyan reviewers rate dialect naturalness, understanding, and risk classification accuracy.
5. **Model comparison** on that set, choosing for understanding and safety, not style alone.
6. **Fallback:** if a phrase is unclear, ask the user to clarify rather than guess. If dialect quality is weak, reply in simple Arabic close to the dialect.

## 5. Model safety

| Layer | Purpose |
|---|---|
| Fixed rules before the model | Detect risk even if the model fails or there is no internet |
| System prompt with clear boundaries | No diagnosis, medication, or dosage. Reminds the user it is a tool, not a human. Gently challenges assumptions instead of people-pleasing |
| Structured output (JSON schema) | The model picks from a fixed list of actions; it does not decide alone |
| Output filter | See section 6 |
| Model settings | Low temperature; provider moderation as an extra layer |
| Red-team set | Risky messages and jailbreak attempts in dialect, run on every prompt change |
| Human review | A mental health specialist reviews the lexicon, exercises, and level 2 responses |

## 6. Output filter

A layered filter, starting with deterministic rules rather than a model.

| Layer | Type | Checks | Cost |
|---|---|---|---|
| 1. Structure check | Code | Valid JSON, action in the allowed list, reasonable length | Instant, free |
| 2. Fixed rules | Code (lexicon + regex) | Means of self-harm, drug names and dosages, diagnosis phrases, medical promises, encouragement of harm | Instant, free, offline |
| 3. Moderation API | Provider model | General self-harm and violence content | Fast, usually free |
| 4. LLM-as-judge | Small fast LLM | Is the reply safe and appropriate for the level? Is it harmfully sycophantic? | Slower and costly; levels 1 and 2 only |

If a reply fails: do not retry the model. Show a pre-written, reviewed safe reply for that level and log the failure locally to improve the rules.

MVP uses layers 1 to 3. Layer 4 is added once tests show how many bad replies pass the first layers. Level 3 needs no filter because the LLM generates nothing.

## 7. Open decisions

- **LLM provider:** decide after the 10-example test.
- **Libyan emergency numbers:** must be verified from an official source before going into the app.
- **Age policy:** 18+, or 13+ with conditions.

## Related

- [Research](../research/README.md)
