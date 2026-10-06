# Design Reference: Wysa Onboarding and Crisis Flow

> Reference screenshots of the Wysa iOS app, captured on 6 October 2026, for future UI/UX work on Manara. Wysa's design and content belong to Wysa; these are for internal reference only and must not be copied into the app.

## Onboarding

| # | Screen | What it does | Note for Manara |
|---|---|---|---|
| 1 | ![](wysa/01-welcome.webp) | Welcome with mascot and one-line promise. Continuing confirms age 13+ and accepts terms. | Short promise; consent and age line at the bottom. |
| 2 | ![](wysa/02-nickname.webp) | Nickname only, "private and anonymous, no login". | Matches our no-account approach. A nickname makes replies personal without real identity. |
| 3 | ![](wysa/03-age.webp) | Age bands: under 13, 13-17, 18+. States it is an AI companion with an optional human coach. | Input for our open age-policy decision; disclose "AI" early. |
| 4 | ![](wysa/04-personality.webp) | Choose tone: Warm or Direct, changeable later; "Maybe later" allowed. | Useful option: Direct mode can reduce the "people-pleasing" complaint. |
| 5 | ![](wysa/05-support-style.webp) | Self-care vs guided support (therapist if affordable). | Maps to our flow: self-help vs being matched to local resources. |

## Chat

| # | Screen | What it does | Note for Manara |
|---|---|---|---|
| 6 | ![](wysa/06-first-chat.webp) | Relaxed first chat, "nothing to fix or fill out", asks what takes most of your time. Voice input and read-aloud. | Low-pressure opener; consider voice input for dialect. |
| 7 | ![](wysa/07-intro-chat.webp) | Short reflective replies while getting to know the user (study, hobbies). | Collects context for topic tracking naturally. |

## Risk and crisis flow

| # | Screen | What it does | Note for Manara |
|---|---|---|---|
| 8 | ![](wysa/08-risk-response.webp) | On an explicit suicidal message, it does not end the chat. It acknowledges and offers quick replies: "Yes, I need more help", "No, just feeling overwhelmed", "You misunderstood", "It's someone else". | Strong pattern for our levels 2-3: a clarifying step that reduces false alarms and helpline fatigue. "It's someone else" handles third-party concern. |
| 9 | ![](wysa/09-crisis-resources.webp) | After confirmation: validating message, states it is a bot not suited for crises, shows helpline cards with "I called" / "I don't want to" follow-ups. | Shows international lines only, not local. Manara should show verified Libyan resources and a trusted-person button, and follow up after the user acts. |

## Key takeaways

1. Anonymous onboarding in under a minute: nickname, age, tone, support style.
2. Early, plain disclosure that it is AI.
3. User-selectable tone (Warm / Direct).
4. Crisis flow uses a clarifying question with quick replies before escalation.
5. Gap Manara can fill: local, verified resources instead of generic international helplines.
