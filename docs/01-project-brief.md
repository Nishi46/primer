# Primer MVP: Project Brief

2026-10-09 · Nishi · Status: draft

## Why we are building it

Two questions need answers from real children before anything more is built:

1. Can speech scoring be trusted at the word level for 5 to 7 year olds?
2. Will parents do the coaching the weekly note asks for?

The MVP is a test, not a product. It is not built to be sold, scaled or guaranteed.

## Who it is for

- **Child, ages 5 to 7.** Reads one short chapter aloud for about 10 minutes a day, four days a week, for four weeks.
- **Parent.** Spends about 5 minutes a week on the note and reads one suggested page with the child.
- **Pilot size:** ten families, one tablet browser, English only.

## What we are building

A web app on a tablet. The child reads a 60 to 120 word chapter of one continuing story aloud and gets word-level highlighting and a fixed hint ladder. She answers one "what happens next?" question, then the app stops. The parent gets one weekly text or email with solid sounds, shaky sounds and one page to read together tonight.

Build effort: about two weeks for one person. Some parts, such as score correction and sending notes, start out done by hand.

## What success looks like

Thresholds are proposed starting points, to be locked before the test begins.

| Question | Pass if |
| --- | --- |
| Can we trust word-level scoring? | App and human listener agree on at least 90% of words, with no age or accent group clearly worse |
| Do children come back? | At least 12 of 16 sessions completed, for most families |
| Do parents coach? | At least half the parents open the note and read the page together in at least 3 of 4 weeks |
| Do children improve? | Most children gain on a hand-scored oral reading and made-up-word check (week 0 vs week 4), and we can say how much |
| Is it safe and calm? | No serious parent concerns after week 4; parents would keep going |

A failed scoring row means changing the scoring approach before building more. A failed coaching row means redesigning the parent layer, or accepting the idea is another solo app.

## Out of scope for version one

- Adaptive lesson ordering per child
- Stories written live for each child
- Free conversation with the child
- Weekly life updates and a parent-editable profile
- Parent app or dashboard
- Automatic progress scoring and published results
- Native apps, other languages, accounts, payments
- Writing, arithmetic, ages 7 and up, the reasoning arc
- Streaks, rewards and "one more" prompts

## Constraints and watch items

- **Cost:** record cost per child per day from the first session.
- **Data:** audio is deleted after scoring unless the parent opts in. The only record per child is a first name, two life details and scores.
- **Content safety:** a human reads every chapter before a child sees it.
