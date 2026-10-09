# Primer MVP: Product Description

2026-10-09 · Nishi

## What it is

The bare-bones Primer is a web app on a tablet where a 5 to 7 year old reads a short chapter of one continuing story aloud, gets word-level feedback, and a parent gets a weekly note on what to do next.

It exists to answer two questions with real children: can speech scoring be trusted at word level, and will parents do the coaching. It is not built to be sold, scaled or guaranteed. Anything that does not help answer those two questions is left out.

## What the child and parent do

The child uses it for about 10 minutes a day, four days a week, for four weeks. The parent spends about five minutes a week.

**The daily session**

1. The child sees a chapter of 60 to 120 words, in large type, that uses only sound patterns taught so far plus a short sight-word list.
2. She reads it aloud. The app listens and highlights each word as she says it.
3. If a word is wrong or skipped, the app waits, then shows the sound, then says the word, then moves on. The ladder is fixed and the same every time.
4. After the chapter, one question: "What do you think happens next?" She answers aloud, and the answer is saved for the parent, not scored.
5. The app says she is done and stops. No streaks, rewards or "one more" prompts.

**The story.** One cast of two characters and one setting run through all 16 chapters. The parent types two lines at signup, such as a pet's name or a fear, and those appear in the chapters.

**The weekly parent note.** A short message, sent by text or email, with three parts: which sound patterns look solid, which are shaky, and one page to read together tonight. It also shows the child's own prediction answers from the week.

## What is in and what is out

| In the first version | Left out until it earns its place |
| --- | --- |
| One fixed sequence of about 16 sound patterns, one per session | Adaptive ordering that changes per child |
| 16 chapters, one cast, written ahead and checked by the decodability script | Stories written live for each child |
| Reading aloud with word-level feedback | Free conversation with the child |
| Two parent-typed life details used in the story | Weekly life updates and a parent-editable profile |
| One weekly text or email note to the parent | A parent app or dashboard |
| A baseline and an end-of-week-4 reading check, run by hand | Automatic progress scoring and published results |
| One tablet browser, English only | Native apps, other languages, accounts, payments |
| Ages 5 to 7, ten families | Writing, arithmetic, ages 7 and up, the reasoning arc |

## How it is built

One person can build this in about two weeks, and several parts can start out done by hand.

- **Front end:** a single web page that shows the chapter, records the microphone and highlights words. No login; each family gets a private link.
- **Speech scoring:** a hosted speech-to-text service that returns word timings, aligned to the known chapter text. The expected text is fixed, so the job is matching, not open transcription. Start with an off-the-shelf model and measure it before fine-tuning anything.
- **Stories:** the language model drafts the 16 chapters once, in advance. The decodability script rejects any sentence that uses an untaught pattern, and a human reads every chapter before a child sees it.
- **Curriculum:** a plain table in code that lists the 16 patterns in order and the sight words allowed at each step. The model never picks the lesson.
- **Parent note:** generated from the week's scores by a template, with the model filling only the one-line summary. Sent by hand or by a script at first.
- **Data kept:** audio is deleted after scoring unless the parent opts in, and the only record per child is a first name, the two life details and the scores.

**Faked by hand at the start.** For the first three families, a person listens to the recordings and corrects the scores, and also acts as the check on the speech service. If the service and the person agree on most words, the automatic version is trusted for the rest.

**Cost to watch.** Record the cost per child per day from the first session, since it decides whether any later price works.

## How we know it works

The test is ten families for four weeks, and the thresholds below are proposed starting points to set before the test begins, not proven standards.

| Question | Measure | Pass if |
| --- | --- | --- |
| Can we trust word-level scoring? | Agreement between the app and a human listener on whether each word was read correctly | At least 90% of words, with no age or accent group clearly worse |
| Do children come back? | Sessions completed out of 16 | At least 12 of 16 for most families |
| Do parents coach? | Weekly notes opened and the suggested page read together | At least half the parents in at least 3 of 4 weeks |
| Do children improve? | Oral reading and made-up-word check at week 0 and week 4, scored by hand | Most children gain, and we can say how much |
| Is it safe and calm? | Parent report after week 4: any distress, any pushing for more screen time | No serious concerns; parents would keep going |

A failure on the first row means changing the scoring approach before building more. A failure on the third means the parent layer needs a redesign, or the idea reduces to another solo app. Either result is useful, and either is cheaper to learn now than after a full build.