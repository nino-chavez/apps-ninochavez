# apps.ninochavez.co — social engagement campaign

Written 2026-08-11, against the live site as shipped. The goal is qualified
testers and real threads, not reach. Both apps are internal alpha — Cutting
Board is invite-only, Yawn 0.4.0 is publicly downloadable but labeled alpha —
so every post is recruitment and positioning, never a GA launch claim.

## What the campaign is selling

Not the apps. The stance. The site's copy already carries a position most of
the market argues against:

- **Local-first, no account.** Files stay on the machine; nothing uploads on
  its own. Against a category racing toward cloud AI everything.
- **"They point; you decide."** Analysis narrows attention and stops. Against
  auto-editing and auto-summarizing.
- **Limits as product facts.** "No promise of completeness." "No substitute
  for consent." The 1.7 GB download exists because the speech runtime is
  on-device. These are the most quotable sentences on the site.

Every post argues one of these three. A post that just announces an app is a
wasted slot.

## Channel plan

Ride the existing syndication engine (`apps/blog/syndication/`); do not build
a new one.

| Channel | Role | Mechanism |
|---|---|---|
| LinkedIn | Primary — where the audience for both stances lives | Campaign one-offs via `post-linkedin-oneoff.mjs`; blog-anchored teasers join `queue.json` automatically once the anchor piece publishes |
| Substack | Anchor essays reach subscribers on the daily drip | Existing `build-queue.mjs` flow — write the piece, the queue picks it up |
| X | Secondary — thread version of the LinkedIn one-offs | `post-x-thread.mjs`, same-day as the LinkedIn post |
| dev.to | Skip | Neither app is a dev tool; the biweekly slot stays with existing writing |

Existing Tue/Thu LinkedIn slots are booked with blog/demo teasers through
2026-09-24. Campaign one-offs go on **Mondays** — clear of the cadence, never
two posts in a day.

## The four posts

Each entry is a brief, not a caption. Captions get drafted under the
signal-dispatch voice guide and must pass `check-captions.mjs` before posting
(source-fidelity gate; the "source" for site claims is the live page copy).

**Mon 2026-08-17 — The stance post (not an announcement).**
*Status: PUBLISHED EARLY, 2026-08-12, by operator call — via
`post-linkedin-oneoff.mjs`, caption at `docs/captions/2026-08-17-linkedin-stance.md`.
Same-day as the Nine RGB Points drip post, overriding this plan's
one-post-per-day rule. The 8/17 Monday slot is now free.*
One argument: tools that point instead of decide. The site is the receipt at
the end, not the subject — its job in the post is to prove the position ships
as working software ("built for my own work, then made available"). No feature
list, no naming both apps beyond a passing line, CTA is the site link only.
Kill rule: if the caption drafts toward "announcing my new apps page," cut
this post and open the campaign with the Yawn consent post on 8/17 instead —
it carries the site link on its own.

**Mon 2026-08-24 — Yawn: the consent post.**
Argues: a meeting record without a meeting bot. The contrast post — no bot
joins the call, no calendar mining, no auto-shared summary, transcript kept as
source rather than presented as claims. Concrete hook: the installer is 1.7 GB
because transcription runs on-device. CTA: download link + "it's an alpha;
tell me where it breaks."

**Mon 2026-08-31 — Cutting Board: the tester call.**
Argues: the sorting is the slow part. A weekend of event video is hours of
scrubbing before the first cut; the board owns that hour and stops where
editorial taste starts. Audience: event/sports video creators. CTA: explicit
invite — alpha is invite-only, DM or email to get a build (macOS and Windows).

**Mon 2026-09-07 — The build story.**
Argues: how these got built — the agent-orchestrated delivery practice, small
tools with hard boundaries. This one wants a blog anchor written first (see
below) so LinkedIn carries the teaser and Substack the full piece. CTA: read
the piece.

## Anchor writing (feeds the engine)

Two pieces, written in the normal blog flow so Substack/LinkedIn/queue handle
distribution without campaign-specific plumbing:

1. **The consent/honest-limits design argument** — why the apps state what
   they can't do on the product surface. Publish before 8/24 so the Yawn post
   can point at it.
2. **The build story** — what it took to ship two alpha apps solo. Publish
   before 9/07.

## Engagement mechanics

- Answer every substantive comment within a day; the corpus shows threads die
  when the author disappears. A comment answered with a real detail
  ("here's the consent screen") outperforms a like.
- Seed each post with one genuine question at the end only when the post
  earns it — never a rote "what do you think?"
- Link discipline: campaign posts link `apps.ninochavez.co` (or the app
  subpage), not the blog, except the build-story teaser.

## Measurement

Outcome first, diagnostics second:

- **Outcome:** Cutting Board tester requests (DMs/emails) and Yawn feedback
  reports with real content. Target is honest: *any* — the funnel is
  unproven; the first four weeks establish the baseline.
- **Diagnostics:** Yawn dmg downloads (R2/Cloudflare analytics), comment
  count per post, site referrals from LinkedIn. Counts are not the result;
  they're the instrument panel.

## Rules that bound the campaign

- Alpha means alpha in every caption. No "launched," no "available now"
  without the internal-alpha qualifier. Same discipline as the evidence-tier
  rule on the main site.
- Every figure in a caption must exist on the site or in the anchor piece.
- No invented interior state; the build story cites commits, not feelings.
- Every post is a command someone runs. Nothing here is scheduled automation.
