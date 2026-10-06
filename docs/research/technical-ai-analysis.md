# Technical AI Analysis: Woebot and Wysa

> Initial concept notes. Each claim is marked **Verified** (supported by public sources), **Partly verified**, or **Unverified** (plausible architecture description, but no public source found). Treat Unverified items as hypotheses, not facts.

## Status note

Woebot's direct-to-consumer app was shut down on 30 June 2025. Woebot Health moved to an enterprise model (access through partner organizations). Its design remains a useful reference, but it is no longer a widely available app. See [sources](#sources).

## 1. Woebot

### Dialogue architecture

| Claim | Status |
|---|---|
| Not free-form generative AI. A rules-based engine that resembles a decision tree of conversational paths; NLP is used only to understand the user's text and pick the best response. | Verified |
| All content is written by conversational designers working with clinical experts, based on CBT, IPT, and DBT. | Verified |
| Dialogue State Tracking (DST) / finite state machine terminology. | Unverified as a published detail; consistent with a decision-tree design |

### Model mechanism

| Claim | Status |
|---|---|
| NLU classifiers extract mood, life events, and emotion type from free text. | Partly verified (NLP for understanding is confirmed; specific models such as BERT are not published) |
| Cognitive-distortion classifier trained on clinically labeled text, triggering a reframing exercise. | Unverified (reframing exercises are confirmed; the dedicated classifier is not documented publicly) |
| Safety classifier running in parallel with each input; above a threshold the conversation is interrupted and the user is routed to a fixed emergency protocol. | Partly verified (concerning-language detection and routing to external resources is confirmed; threshold design is not published) |

### AI-driven features

- Guided cognitive restructuring: identify a negative thought, reframe it, and re-measure. (Partly verified)
- Mood tracking over time linked to context such as work, family, and sleep. (Partly verified)

## 2. Wysa

### Dialogue architecture

| Claim | Status |
|---|---|
| Hybrid of NLP/NLU understanding plus pre-written, clinician-audited responses. Sources state Wysa does not use generative models for clinical content. | Verified (older sources; the current product may differ, so recheck) |
| A rules engine and content library built from millions of conversations, with clinical safety testing. | Verified |
| Safety enforced by a deterministic layer separate from the language model. | Partly verified (described in general terms for safe chatbot design) |
| "Policy engine" over CBT/DBT evidence base, and a "reflective generative" listening engine with strict constraints. | Unverified; conflicts with the sources above on generative use |

### Model mechanism

| Claim | Status |
|---|---|
| Each AI model validated on at least 10,000 manually tagged records not in the training set. | Verified |
| Meets the NHS UK DCB 0129 clinical safety standard. | Verified |
| Multi-dimensional emotion engine (valence, arousal, energy, hopelessness) using fine-tuned transformers. | Unverified |
| Contextual recommendation engine choosing the exercise (breathing, journaling, grounding). | Partly verified (tool selection by context is described; internals are not) |
| Constrained adaptive personalization from user response and satisfaction. | Unverified |
| "150+ tools" count. | Unverified; check the current Wysa site |

## 3. Technical comparison

| Criterion | Woebot | Wysa |
|---|---|---|
| Core architecture | Rules-based decision tree plus NLU | NLU plus rules engine plus clinician-written content library |
| Generative text | None in clinical dialogue | Reported none for clinical content (verify current status) |
| Classifier focus | Intent matching and, reportedly, cognitive distortions | Emotion and distress level, and matching the case to an exercise |
| Safety triage | Concerning-language detection routing to outside resources | Distress detection routing to emergency or local crisis resources |
| Availability | Consumer app closed 30 June 2025 | Active |

## 4. Lessons for Manara

| Lesson | Application |
|---|---|
| Separate understanding from decisions | The LLM classifies and converses; a fixed rule layer decides escalation. |
| Keep clinical content pre-written | Exercises come from a vetted library; the model selects, not invents. |
| Deterministic safety layer | Rule-based risk detection and static emergency screen, independent of the model. |
| Validate models on held-out data | Build a tagged Libyan-dialect test set (at least 10,000 records is Wysa's bar; start with the 10-example pilot). |
| Avoid pure rule-based rigidity | Users complain about canned responses, so allow open conversation while constraining actions. |
| Plan for regulation | Woebot cited the cost of FDA authorization and unclear rules for LLM tools; position Manara as guidance, not treatment. |

## Sources

- [IEEE Spectrum: Do We Dare Use Generative AI for Mental Health?](https://spectrum.ieee.org/woebot)
- [MobiHealthNews: Q&A on mental health chatbot safety guardrails (Wysa)](https://www.mobihealthnews.com/news/qa-why-mental-health-chatbots-need-strict-safety-guardrails)
- [Wysa: AI self-help](https://www.wysa.com/ai-self-help)
- [MobiHealthNews: Woebot Health shutting down its app](https://www.mobihealthnews.com/news/woebot-health-shutting-down-its-app)
- [Telehealth.org: What Woebot's exit signals](https://telehealth.org/news/ai-psychotherapy-shutdown-what-woebots-exit-signals-for-clinicians/)

## Related

- [Competitor feature analysis](competitor-analysis.md)
- [User research and motivation](user-research.md)
- [AI support usage findings](ai-support-usage-findings.md)
