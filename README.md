<picture>
  <source media="(prefers-color-scheme: dark)" srcset="media/banner-dark.png">
  <img alt="CareerOS. Your work, on the record. An evidence-first career record: it drafts only what your work can prove, and publishes only what you approve." src="media/banner-light.png">
</picture>

<br>

CareerOS notices when you ship. It drafts your résumé line, site news, GitHub README line and
LinkedIn caption **only from facts it can show**, keeps every line beside its proof, and
publishes nothing until you approve it.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="media/hero-dark.png">
  <img alt="The review screen on a laptop and a phone: drafts for each place on the left, the claims and evidence behind them on the right, and a bar to approve, snooze or dismiss." src="media/hero-light.png">
</picture>

> Every image here is a screenshot of the real app, signed in to a demo account with fictional
> people and work. The images follow your GitHub theme, the way the app follows your system.

### It notices, and says why

A release or a merged pull request arrives and lands in your queue with the reason it is there.
The top three are *Start here*: what matters most, while the details are fresh, and quickest to
decide. No scores, no streaks.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="media/notices-dark.png">
  <img alt="Start here: two releases, each with the reason it is first, how long it takes to decide, and the places a draft is ready for." src="media/notices-light.png">
</picture>

### Every line keeps its receipts

Each draft cites the facts it rests on. Seven checks in code (numbers, attribution, citations,
privacy, links, length, style) run before you see it, and anything the AI inferred stays marked
until you confirm it. An evaluation suite of real and adversarial cases runs on every change.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="media/receipts-dark.png">
  <img alt="A résumé line draft with its Include switch and passed checks, beside the claims that support it: one verified from GitHub, others waiting for confirmation." src="media/receipts-light.png">
</picture>

### Ready for LinkedIn, posted by you

LinkedIn doesn't let apps post for you, and CareerOS never scrapes it. Approve LinkedIn text and
you get the caption plus a card image made only from the facts that post cites: copy, save,
post, mark it posted.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="media/linkedin-dark.png">
  <img alt="The LinkedIn hand-off: the caption, four numbered steps, and a generated card showing the achievement, its project and the facts behind it." src="media/linkedin-light.png">
</picture>

### One record, every place it goes

Your website reads your approved news, projects and profile through a public API, feeds and a
web component, so a portfolio keeps itself up to date. Your GitHub profile README gets a short
block between two markers. Résumés export as PDF, Word and JSON Resume. Each place says whether
it updates by itself or waits for you.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="media/channels-dark.png">
  <img alt="Channels: an index of GitHub, the public profile, the README, LinkedIn and site rebuilds, beside the public profile with exactly what a visitor's site receives." src="media/channels-light.png">
</picture>

### Made for the phone as well

Each screen changes shape on a small display instead of shrinking: one column, the decision in
reach above the tab bar, the detail one tap away.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="media/phones-dark.png">
  <img alt="Three phones: the Desk with what to start on, a review with its approve bar, and Channels with the LinkedIn hand-off." src="media/phones-light.png">
</picture>

## How it is built

| | |
|---|---|
| Web | Next.js 16 (App Router) and React 19, server actions, a strict nonce-based Content Security Policy |
| Data | PostgreSQL 17 with Drizzle; every record versioned, every change in an append-only history |
| Jobs | A Postgres-backed worker with leases, retries and dead letters |
| AI | Any provider or none (templates). Publishing rules are code, never prompts, with an evaluation suite in CI |
| Public API | Read-only and approved items only; JSON, JSON Feed, RSS, a TypeScript SDK and a web component |
| Quality | Unit and integration tests on a real database, Playwright journeys with axe accessibility checks, a Docker compose smoke test, all in CI |
| Design | Fraunces, Instrument Sans and Newsreader; Hugeicons; a seal for a logo; light and deep dark themes from one set of tokens |

## Status

| | |
|---|---|
| Web app | Built and running locally. **Not deployed**: there is no public instance yet. |
| Mobile app | Not built yet; the app API, tokens and screen spec are ready for it. |
| GitHub | Integration built and tested with signed webhook fixtures; the GitHub App itself is not registered yet. |
| Name | "CareerOS" is a working name. |

The source code is private.

<details>
<summary><strong>Every screen, light and dark</strong></summary>

<br>

| Light | Dark |
|---|---|
| ![Landing page](screenshots/landing.png) | ![Landing page, dark](screenshots/landing-dark.png) |
| ![Desk](screenshots/desk.png) | ![Desk, dark](screenshots/desk-dark.png) |
| ![Review queue](screenshots/review-queue.png) | ![Review queue, dark](screenshots/review-queue-dark.png) |
| ![Review](screenshots/review-detail.png) | ![Review, dark](screenshots/review-detail-dark.png) |
| ![Activity](screenshots/activity.png) | ![Activity, dark](screenshots/activity-dark.png) |
| ![Vault](screenshots/vault.png) | ![Vault, dark](screenshots/vault-dark.png) |
| ![Channels](screenshots/channels.png) | ![Channels, dark](screenshots/channels-dark.png) |
| ![Public profile channel](screenshots/channels-site.png) | ![Public profile channel, dark](screenshots/channels-site-dark.png) |
| ![History](screenshots/history.png) | ![History, dark](screenshots/history-dark.png) |

| Phone | | |
|---|---|---|
| ![Desk on a phone](screenshots/phone-desk-light.png) | ![Review on a phone](screenshots/phone-review-light.png) | ![Channels on a phone](screenshots/phone-channels-light.png) |
| ![Desk on a phone, dark](screenshots/phone-desk-dark.png) | ![Review on a phone, dark](screenshots/phone-review-dark.png) | ![Channels on a phone, dark](screenshots/phone-channels-dark.png) |

</details>

## Licence

This README and its images are released under the [MIT licence](LICENSE). The CareerOS source
code is private and is not covered by it.
