# spice-bets

The public site for a paper betting log: every pick graded against the closing line, including
the sports where that number is negative.

Live at — *(set once the host is connected)*

## This directory is generated. Do not edit it by hand.

Every `.html` file here is written by `build-site.ps1`, which lives one level up and reads its
data from two places:

| source | what it supplies |
|---|---|
| `clv-tracker.html` | the 711-pick log — soccer, college football, MLB, NFL, NHL |
| `nba-paper.psv` | the NBA shadow book, which is not in the tracker |

Neither source is in this repo, and neither should be. A hand-edit here survives exactly until
the next rebuild, and in the meantime it makes the site disagree with the log it is supposed to
be reporting — which is the precise failure this whole arrangement exists to prevent.

To change the site, change the builder.

## How it updates

`build-site.ps1` runs off the end of the nightly grading job. It is triggered by a **SHA-256 of
its inputs**, not by file timestamps: one of the upstream scripts rewrites its data file
byte-identically on every run, so a timestamp check fires forever and means nothing.

## Why the commit history matters

The site's claim is that records are frozen once graded and never re-priced. A public, timestamped
commit log is the proof of that claim — anyone can check that the number shown on a given date was
in fact the number shown on that date. That is the point of hosting it in the open, and it is why
nothing here is ever rewritten after the fact.

## What is deliberately absent

No stakes, no bankroll, no unit sizes — this is a paper log and none of it is a record of money
risked. No crowned play of the day. No sportsbook comparison. The screeners, the gate studies and
the pre-registrations stay out of this repo entirely; only the generated pages are published.
