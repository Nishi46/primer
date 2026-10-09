# Primer MVP: Product Requirements

2026-10-09 · Nishi · Status: draft, open questions resolved · Builds on [01-project-brief.md](01-project-brief.md)

Every story is tagged **MVP** (in the first version) or **Manual** (done by a person at first). Decisions that [mvp.md](mvp.md) left open were settled on 2026-10-09 and are recorded in the Decisions table at the end.

## Roles

| Role | Who | Where they act |
| --- | --- | --- |
| Child | Age 5 to 7, reads aloud | Tablet browser, private link |
| Parent | Signs up, receives the note, coaches | Signup page, text or email |
| Operator | Nishi | Behind the scenes: reviews recordings, sends notes, runs reading checks |

## Child stories

**C1. Read the chapter.** As a child, I see a chapter of 60 to 120 words in large type so I can read it aloud. *(MVP)*
- Text uses only sound patterns taught so far plus the allowed sight words.
- The chapter is the next unread one in the fixed sequence.

**C2. See where I am.** As a child, I see each word highlighted as I say it. *(MVP)*
- The highlight follows the word being read.
- Correct words highlight normally. A missed word gets no red mark and no "wrong" message; the ladder simply begins on it.

**C3. Get help on a hard word.** As a child, when a word is wrong or skipped I get the same help every time. *(MVP)*
- The ladder is fixed: wait, then show the sound, then say the word, then move on.
- The ladder never changes by child or by day.
- Timing: wait 3 seconds, show the sound for 3 seconds, then say the word and move on. The child does not repeat the word. Timings are tunable constants.
- A word that reached any rung counts as not read correctly for scoring.

**C4. Say what happens next.** As a child, after the chapter I answer "What do you think happens next?" aloud. *(MVP)*
- The answer is recorded and saved for the parent. It is not scored.
- The audio is transcribed; the text is kept for the parent and the clip is deleted unless the parent opted in to audio.

**C5. Know when I'm done.** As a child, I'm told I'm done and the app stops. *(MVP)*
- No streaks, rewards, badges or "one more" prompts.
- Only one session per child per day; a second start the same day is blocked. Missed days are not made up: the sequence waits for the next day.

**C6. Pick up where I left off.** As a child, if the session is interrupted I can come back. *(MVP)*
- An interrupted session resumes from the last word. It counts as completed only once the chapter and prediction question are finished.

## Parent stories

**P1. Sign up.** As a parent, I enter my child's first name and two life details (such as a pet's name or a fear) and where to send the weekly note. *(MVP)*
- No account, password or payment.
- The parent chooses text or email for the link and the weekly note, and consents to that channel at signup.

**P2. Get a private link.** As a parent, I receive a private link for my child's tablet. *(MVP)*
- The link works without a login and identifies one child.
- Only the parent and child have the link.

**P3. See my child in the story.** As a parent, the two details I typed appear in the chapters. *(MVP)*
- Details are placed into pre-written chapters at fixed slots. Nothing is written live.
- I cannot edit them after signup.

**P4. Get the weekly note.** As a parent, once a week I get a short message with: sounds that look solid, sounds that look shaky, one page to read together tonight, and my child's prediction answers from the week. *(MVP)*
- Built from a template; the model fills only the one-line summary.
- "One page" is a pre-written excerpt of the story, chosen from the child's shaky sound patterns, for parent and child to read aloud together.

**P5. Control audio.** As a parent, I can opt in to keeping my child's recordings. *(MVP)*
- Default is audio deleted after scoring.
- The choice is made at signup. Revocation handling is a technical-design item.

**P6. Give feedback at the end.** As a parent, after week 4 I report any distress or pushing for more screen time and whether we would keep going. *(Manual)*

## Operator stories

**O1. Correct scores.** As the operator, for the first three families I listen to recordings and correct word scores, so the speech service is checked against a person. *(Manual)*
- Record the app's call and my call per word, so agreement can be computed.

**O2. Send notes.** As the operator, I send the weekly note by hand or by script. *(Manual)*

**O3. Run reading checks.** As the operator, I run and score a baseline at week 0 and a repeat at week 4: oral reading plus made-up words. *(Manual)*

**O4. Track cost.** As the operator, I see cost per child per day from the first session. *(MVP)*

**O5. Review chapters.** As the operator, I read every chapter before any child sees it, after the decodability script has passed it. *(Manual)*

## System behavior

| # | Rule |
| --- | --- |
| S1 | 16 sound patterns in fixed order, one per session; the sequence is a plain table in code. The model never picks the lesson. |
| S2 | 16 chapters, one cast of two characters, one setting, written ahead. |
| S3 | The decodability script rejects any sentence using an untaught pattern or non-listed sight word. |
| S4 | Speech scoring aligns recognized words to the known chapter text; it is matching, not open transcription. |
| S5 | A word is correct, wrong or skipped. Scores per word are stored per session. |
| S6 | Audio is deleted after scoring unless the parent opted in. |
| S7 | Per child, the only stored record is first name, two life details and scores (plus anything S6 or C4 requires). |
| S8 | English only, iPad with Safari. |

## Decisions

| # | Question | Decision |
| --- | --- | --- |
| Q1 | Hint ladder timing and scoring | Wait 3s, show sound 3s, say word, move on; no repeat; any rung reached counts as not correct |
| Q2 | Sessions per day, make-up | One per day; no make-up |
| Q3 | Prediction answer vs. audio deletion | Transcribe, keep text, delete audio unless opted in |
| Q4 | Interrupted session | Resume from last word; complete only when chapter and question are done |
| Q5 | Missed-word display | Neutral; no "wrong" message |
| Q6 | Note and link delivery | Parent's choice of text or email |
| Q7 | "One page to read together" | A page of the story, chosen from shaky patterns |
| Q8 | Device | iPad + Safari |

## Follow-ups for later documents

- **Technical design:** SMS provider and phone consent; audio-opt-in revocation; transcription service for the prediction answer.
- **UX flows:** how a resumed session looks; what the child sees when a second same-day start is blocked.
- **Content:** the story needs excerpt-sized pages so the parent page can be picked for any shaky pattern.
