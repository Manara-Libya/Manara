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

## Next step

Write the system prompt and output schema, then test models on 10 Libyan-dialect examples.

## Disclaimer

Manara is a guidance and support tool, not a substitute for professional care. In an emergency, contact the relevant authorities immediately.
