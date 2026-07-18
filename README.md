# Pocket Planner (The Comeback Plan)

A private, mobile-first budgeting + debt-payoff web app for a small accountability group
(2 members + 1 coach). Manual entry only — no bank linking, ever.

## Live pieces

- **Front-end:** `index.html` in this folder, hosted on GitHub Pages
  (repo: `dngueyadata-sudo/pocket-planner`).
- **API + database:** Supabase project `comeback-plan` (ref `txrfewxihlqrpoatelvn`, free tier),
  one edge function named `app` (custom username+PIN auth, PBKDF2-hashed, 60-day sessions).
  All tables have RLS enabled with no policies — only the edge function (service role) can
  touch data. HTML cannot be served from *.supabase.co (platform anti-phishing rule),
  which is why the front-end lives on GitHub Pages.

## Invite codes

Stored in the `app_config` table (change them there):
- member code: `COMEBACK26`
- coach code: `COACH26` (keep private — coach sees the Team dashboard)

## Features (v1)

- Paycheck-based plan: take-home per paycheck, next payday, flexible allowance, bills list.
- Home: "flexible money left until payday" + per-day pace, quick log (3 taps), no-spend days,
  logging streaks, extra-income (overtime/side gig) tracking.
- Debts: cards with balance/APR/min payment, snowball vs avalanche comparison, debt-free date,
  payoff order, log payments with celebration.
- Coach Team view: per-member streaks / budget / debt progress, honoring each member's
  privacy tier (Everything / Summary only / Streaks only) — members control this in More.

## Not yet built (v2 ideas)

- Pause List (48-hour impulse brake with "money saved by waiting" tally)
- Printable weekly paper worksheet
- Friendly competition view

## Maintenance notes

- Free-tier Supabase projects pause after ~1 week of inactivity; restore from the
  Supabase dashboard or via MCP (`restore_project`) if the API stops responding.
- Edge function source is retrievable via the Supabase MCP (`get_edge_function`).
