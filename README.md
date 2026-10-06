# Manara

> **Note:** This is the initial concept for Manara. It is a work in progress, and more ideas will be added to it.

A personal emotional-support companion app for young people in Libya.

## Problem

Mental health support is hard to reach in Libya, and stigma stops many young people from asking for help.

## How it works

- **Supportive chat:** Listens and empathizes in a Libyan-friendly Arabic dialect, with no medical diagnosis.
- **Mood and topic tracking:** Spots patterns over time, for example stress during exams.
- **Local resource matching:** Guides users to a verified local directory of specialists, hotlines, and university support.
- **Three-level escalation:**
  1. Normal support.
  2. Suggested contact with a ready-made message.
  3. An urgent fixed screen with emergency numbers and a "trusted person" button.

## Planned features

Inspired by existing products. See the [research folder](docs/research/README.md) for the competitor analysis, user research, usage findings, and technical AI analysis.

| Feature | Inspired by | Manara implementation |
|---|---|---|
| Anonymous use | Wysa | No account or sign-up |
| Pre-reviewed techniques | Woebot | Model selects from a fixed set of vetted exercises |
| Risk-language detection | Woebot | Rule-based detection plus a fixed emergency screen |
| No autonomous decisions | Wysa | User always decides; nothing is sent without consent |
| Resource matching | Shezlong | Match the problem to a local support resource |
| Emotional pattern tracking | Shezlong | Weekly mood indicators |
| Cultural and language adaptation | Wysa (Dreamkit) | Libyan dialect and local resources |
| Not-a-diagnosis notice | Wysa | Clear message on first use |
## Tech

- Flutter app
- Encrypted local storage
- LLM API for chat and classification
- Embeddings with RAG for resource matching
- Fixed rule-based risk detection

## Privacy by design

- No account needed.
- Data stays on the device.
- Personal details are masked before reaching the model.
- Nothing is sent to anyone without the user's consent.

## Design

See the draft [system design](docs/design/system-design.md): message pipeline, escalation levels, Libyan dialect approach, and safety layers.

## Next step

Write the system prompt and output schema, then test models on 10 Libyan-dialect examples.

## Disclaimer

Manara is a guidance and support tool, not a substitute for professional care. In an emergency, contact the relevant authorities immediately.








