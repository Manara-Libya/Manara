# User Research and Motivation

> Initial concept notes. Findings come from Reddit discussions (for example r/Libya and r/mentalhealth) and are anecdotal, not a formal study.

## Why Manara exists

Young people in Libya face stigma, cost, and limited access to trusted specialists. Many turn to chatbots because they are private, always available, and free of judgment. Existing apps are not built for Libyan dialect, local resources, or on-device privacy. Manara aims to fill that gap by guiding users to real local support rather than trying to replace it.

## 1. Problems that push users toward these apps

| Problem | What users say | What it means for Manara |
|---|---|---|
| Stigma and fear of social judgment | In communities such as r/Libya, users repeatedly say it is hard to tell family or acquaintances about mental health issues, for fear of being dismissed or judged. A bot becomes a judgment-free zone. | Anonymous use, no account, no sharing without consent. |
| Anxiety and stress late at night | Users in r/mentalhealth describe needing someone to listen late at night (venting or panic moments) when no counselor or friend is reachable. | Always-available supportive chat. |
| Cost and difficulty reaching specialists | Sessions are expensive and it is hard to find a certified, trusted specialist locally. An assistant acts as first-line triage and support. | Verified local resource directory and matching. |

## 2. Similar apps and user experiences

Of the apps reviewed, **Wysa and Woebot are the most widely used and best known**.

### Wysa and Woebot

- Based on guided cognitive behavioral therapy (CBT); chatbots give immediate stress-management exercises.
- **User feedback:** very good for easing temporary anxiety and for journaling.
- **Common complaint:** responses can feel repetitive and scripted (canned responses).

### Open-ended chat models (such as ChatGPT used for emotional support)

- Used to unload and organize confused thoughts and to ask for coping strategies.
- **User feedback:** praised for flexible listening and empathy.
- **Common complaint:** an excessive tendency to agree and please (people-pleasing) instead of guiding users toward decisive steps.

**Takeaway for Manara:** combine the safety of structured, vetted techniques (Wysa, Woebot) with the natural, empathetic conversation of open-ended models, while avoiding people-pleasing.

## 3. Technical and ethical challenges raised by Reddit users

| Challenge | Details | Manara response |
|---|---|---|
| Lost context and limited memory | Users must re-explain their situation every session when there is no persistent, encrypted memory. | Encrypted local storage with on-device memory. |
| Privacy and data retention | The biggest fear is that sensitive chats are stored and used to train models. Full encryption is seen as necessary for honest conversation. | Data stays on device; personal details masked before reaching the model. |
| Boundaries and human triage | Most participants see AI's best value as an organizing and triage tool that leads to real resources (emergency numbers, clinics, support groups), not a final replacement for a doctor. | Three-level escalation and verified local directory; no diagnosis. |

## Related

- [Competitor feature analysis](competitor-analysis.md)
- [AI support usage findings](ai-support-usage-findings.md)

