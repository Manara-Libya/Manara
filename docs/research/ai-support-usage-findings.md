# AI Support Usage Findings (Reddit)

> Initial concept notes. Findings come from discussions in r/therapyGPT and r/mentalhealth about using AI as an emotional-support tool. They are anecdotal user reports, not a formal study.

## 1. How people actually use AI for support

| Pattern | Description | Why it matters |
|---|---|---|
| The "2 AM" gap | Panic attacks and rumination often happen late at night, when no specialist or friend is reachable. The assistant acts as a safety valve to release emotions in real time. | Manara must be available at any hour and work with a phone alone. |
| Cognitive sorting | Users write confused, disconnected paragraphs and ask the model to summarize them and untangle cognitive distortions (such as catastrophizing), which lowers stress immediately. | Include a "sort my thoughts" flow that summarizes and reflects back. |
| Unmasking | Where stigma is strong, users share details and trauma with a model that they are ashamed to share with a human therapist or family, to avoid pity or judgment. | Anonymous use and strong privacy are a precondition for honesty. |

## 2. Technical and behavioral problems reported by the community

| Problem | Complaint | Impact on the user | Manara response |
|---|---|---|---|
| Sycophancy | Models tend to agree with the user and justify their actions instead of questioning them. | An echo chamber that reinforces a victim mindset instead of addressing behavior. | Prompt the model to act as an objective facilitator that gently challenges assumptions. |
| Parasocial bond | Users become emotionally dependent on excessive empathy and treat the AI as a real friend or family substitute. | More social isolation and difficulty ending the dependency later. | Explicit identity boundaries and periodic reminders that Manara is a thinking tool. |
| Helpline fatigue | The chat is cut off abruptly and emergency numbers are sent when users express deep sadness, without assessing actual risk. | Users feel misunderstood, treated as a security risk, and stop asking for help. | Graduated escalation that does not abruptly end the conversation. |
| Memory and privacy dilemma | Fear that sensitive data trains models, versus frustration at the system forgetting context and having to re-explain trauma each session. | Hesitation to be fully honest, or frustration with cold, forgetful replies. | Encrypted on-device memory with user-controlled deletion. |

## 3. Technical requirements for a local implementation

### Prompt architecture

- Configure the model as an **objective facilitator**, not an overly sympathetic therapist. It should politely challenge incorrect assumptions rather than go along with them.
- Enforce **explicit identity boundaries**: continually remind the user that this is an organizing and thinking tool, not a human.

### Contextual triage

- Distinguish accurately between ordinary emotional venting and explicit physical danger.
- Move the user toward outside support (specialists, helplines) gradually, without shocking or ending the conversation.

### Strict data security (zero retention)

- End-to-end encryption.
- Immediate deletion of chat history on request.
- User data isolated from any later model training, so young people can use the app without fear of their sensitive context leaking.

## Related

- [User research and motivation](user-research.md)
- [Competitor feature analysis](competitor-analysis.md)

