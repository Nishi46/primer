# Primer

A web app on a tablet where a 5 to 7 year old reads a short chapter of one continuing story aloud, gets word-level feedback, and a parent gets a weekly note on what to do next.

**Status:** planning. No code yet. This is a research pilot (ten families, four weeks), not a product. It exists to answer two questions: can word-level speech scoring be trusted for young children, and will parents do the coaching.

## Documents

Read in this order:

1. [MVP description](docs/mvp.md)
2. [Project brief](docs/01-project-brief.md): why, who, success, out of scope
3. [Product requirements](docs/02-prd.md): stories and system rules
4. [UX flows and screens](docs/03-ux-flows.md)
5. [Data model](docs/04-data-model.md)
6. [Technical design](docs/05-technical-design.md): stack decisions

## Planned stack

- Front end: small framework with Vite, iPad Safari only
- Speech scoring: general speech-to-text aligned to the chapter text
- Hosting and data: backend-as-a-service
- Delivery: email and SMS by script

Vendors are not chosen yet. See the technical design.

## Prerequisites

To be filled in when the build starts. Expected:

- Node.js (version to be set)
- An account on the chosen backend platform
- API keys for the speech service, email provider and SMS provider
- A real iPad with Safari for testing the microphone

## Setup

```sh
# To be written once there is code.
# 1. Clone the repo
# 2. Install dependencies
# 3. Copy the example environment file and add keys
# 4. Start the dev server
```

## Repository layout

Current:

```
README.md
LICENSE
docs/        planning documents listed above
```

Planned: front-end app, backend functions, curriculum table, chapter drafts, decodability script, operator tools.

## Privacy

The pilot involves children's voices and names. Audio is deleted after scoring unless a parent opts in, and the only per-child record is a first name, two life details and scores. Scores, transcripts and parent contact details are deleted 90 days after the pilot ends. Do not commit recordings, real names, contact details or API keys.

## License

[MIT](LICENSE)
