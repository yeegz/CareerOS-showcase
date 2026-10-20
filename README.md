# CareerOS

**Your work, on the record.** CareerOS is an evidence-first career record. It notices when you ship
(a GitHub release, a merged pull request), drafts your résumé line, site news, README line and LinkedIn
text **only from claims it can back with evidence**, and publishes nothing until you approve it.

> This repository is the public showcase: screenshots, the design and the honest status. The source code
> lives in a private repository.

![The review screen: drafts on the left, the proof behind them on the right](screenshots/review-detail.png)

## Status (October 2026)

| | |
|---|---|
| Web app | Built and working **locally** (Next.js 16, PostgreSQL). **Not deployed**: there is no public instance yet. |
| Tests | 431 automated tests pass (unit and integration against a real PostgreSQL database), plus an evaluation suite for the publishing gates. |
| Mobile app (Flutter) | **Not built yet.** The app API, design tokens and screen spec are ready for it. |
| GitHub integration | Implemented and tested with signed webhook fixtures; the GitHub App itself is not registered yet. |
| AI drafting | Works with a provider key; without one, it falls back to templates. Either way, every draft passes the same code-based gates. |
| Name | "CareerOS" is a working name. |

Everything in the screenshots is the real app running against a seeded demo account ("Ada Example"); the
people, repositories and work in it are fictional.

## What it does

- **Vault.** Your profile, projects, experience, education, achievements, skills, certifications and
  evidence in one place, every change versioned.
- **Sources.** GitHub releases and merged pull requests arrive in Activity, each with a plain reason why
  it was or was not suggested. Nothing publishes because a webhook arrived.
- **Review.** Each suggestion shows what happened, the claims behind it (verified, needs your
  confirmation, out of date), the evidence, and a draft per channel. You confirm claims, edit wording,
  choose channels and approve. Unconfirmed claims cannot be published.
- **Gates, in code, not prompts.** Numbers, attribution, citations, privacy, links, length and style are
  checked before anything can be approved. The AI may never invent a metric, a role or an outcome.
- **Publishing.** Your public profile and news feed (JSON, JSON Feed, RSS) for your own website through a
  public API and SDK, a managed block in your GitHub profile README, and LinkedIn text you copy and post
  yourself (LinkedIn offers no API for this, and CareerOS never scrapes it). Deleting a record retracts
  what it published.
- **Recommendations you can see the reasons for.** The queue is ranked by significance, freshness, effort
  and momentum, with the top three as "Start here", each with its reasons. Scores are never shown. Your
  past decisions tune it.
- **For developers.** Scoped API keys, signed outbound webhooks and an OpenAPI reference.

## Screens

| | |
|---|---|
| ![Landing page](screenshots/landing.png) | ![Desk](screenshots/desk.png) |
| **Landing.** One promise, one example with its proof; the seal stamps "Approved by you". | **Desk.** What to do next, ranked, with the reason for each. |
| ![Review queue](screenshots/review-queue.png) | ![Activity](screenshots/activity.png) |
| **Review queue.** Rank, one plain reason, effort, and which channels have drafts. | **Activity.** Everything GitHub reported, and why it was or was not suggested. |
| ![Channels](screenshots/channels.png) | ![Public profile channel](screenshots/channels-site.png) |
| **Channels.** Every destination with where it stands; opens on what needs you. | **Your site.** What visitors would see, and the exact data your site receives. |
| ![Vault](screenshots/vault.png) | ![History](screenshots/history.png) |
| **Vault.** Your record by kind; each item knows what still needs you. | **History.** Every edit, decision, publication and permission. |

### Dark mode

| | |
|---|---|
| ![Review in dark mode](screenshots/review-detail-dark.png) | ![Desk in dark mode](screenshots/desk-dark.png) |

### Phone

| | | | |
|---|---|---|---|
| ![Desk on a phone](screenshots/phone-desk-light.png) | ![Review on a phone](screenshots/phone-review-light.png) | ![Desk on a phone, dark](screenshots/phone-desk-dark.png) | ![Review on a phone, dark](screenshots/phone-review-dark.png) |

## Design

- **Idea:** a record with receipts. Every published line sits beside the proof it rests on.
- **Logo:** a seal, the stamp you press when you approve, with the app's proof mark at its centre, and
  lowercase lettering drawn on the same round grid.
- **Type:** Fraunces with soft corners for headings, Instrument Sans for the interface, Newsreader for
  the words you will publish.
- **Icons:** Hugeicons Stroke Rounded, the same set planned for the mobile app.
- **Shape and motion:** soft radii (12 for controls, 20 for cards, 24 for sheets); the seal's stamp and
  the proof mark's press are the only signature motions; reduced motion is respected.
- **Status in words, not dots:** "Needs you", "Watching", "In review".
- **Accessibility:** keyboard-first, visible focus, 44 px targets, contrast checked by tests in both
  themes.

## How it is built

| Layer | Choice |
|---|---|
| Web | Next.js 16 (App Router), React 19, server actions; no client secrets |
| Data | PostgreSQL 17, Drizzle ORM, versioned records and an append-only history |
| Auth | Better Auth (email and password, GitHub), bearer tokens for the mobile app |
| Jobs | A Postgres-backed worker with leases, retries and dead letters |
| AI | Provider-agnostic drafting behind deterministic gates, with an evaluation suite |
| Public API | Read-only, published items only, with a TypeScript SDK and a web component |
| Tests | Vitest (unit and integration against a real database) |

## Licence

The contents of this showcase repository (this README and the screenshots) are released under the MIT
licence. The CareerOS source code is private and is not covered by it.
