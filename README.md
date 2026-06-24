# traction-triage

Turn a messy daily task dump into a sane, prioritized day plan for a boutique
design/dev agency — grounded in **EOS** (the Entrepreneurial Operating System
from *Traction* by Gino Wickman - not officially endorsed and not affiliated).

Built for the agency reality EOS doesn't model out of the box: running **client
delivery + internal products + business-building** at the same time, with a small
team and AI agents to delegate to.

---

## The problem it solves

EOS has **no daily layer by design**. Its cadences are quarterly (**Rocks**) and
weekly (**L10 meeting**, **Scorecard**, **7-day To-Dos**). A daily brain-dump is
not an EOS object — so the skill's whole job is the *bridge*: force every task to
resolve to one of five EOS fates, then assemble a day that protects what matters.

| Fate | Meaning |
| --- | --- |
| **Eliminate** | Advances nothing. Kill it. |
| **Delegate** | Team, AI agent, or contractor should own it — not you. |
| **Rock work** | Advances a 90-day priority. Protect this time first. |
| **To-Do** | Concrete, single-owner, doable in ≤7 days. |
| **Issue** | Needs a decision/discussion. Park it; solve weekly via IDS — never reactively. |

The two things that make it work where vanilla EOS fails: a **Hat/P&L tag** (so
billable fires don't starve the product Rocks) and a **$/hour band** (so $10 work
still on your plate gets flagged as a delegation miss).

---

## Install

- [ ] Copy the `traction-triage/` folder into your skills directory (e.g. your Giant Brains repo).
- [ ] Confirm `SKILL.md` sits at `traction-triage/SKILL.md`.
- [ ] No dependencies, scripts, or config files — it's a single-file skill.

---

## Use

It triggers on any "make my day sane" prompt — you don't have to say *EOS* or *Traction*:

- "Triage my day" · "plan my day" · "what should I work on"
- "Sort this to-do list" · "I'm drowning in tasks" · "too much on my plate"
- Paste a brain-dump, an inbox, or a rebalance-OS / Linear / GitHub feed.

**Example**

Input:
> fix Binoid checkout bug; reply to 14 emails; write the Hypercart query-guard docs
> (Rock); pick a logo color for the meetup deck; teammate asked about invoicing;
> research new CI tool; weekly client status report.

Output (excerpt): the Hypercart Rock gets a protected 90-min block *first*; the
Binoid bug is the one client commitment; emails batch into 15 minutes; the logo
color and invoicing question are delegated to an agent and ops; "which CI tool"
is parked as an **Issue** for the next L10; the weekly status report is flagged
to **systematize** as a Core Process.

---

## Make it yours (Step 0 context)

The skill runs best when it knows three things. Supply them in-prompt, or let it
infer and flag assumptions:

- [ ] **Current Rocks** — this quarter's 3–7 priorities. No Rocks? It infers 1–3 provisional ones from your product lines and says so.
- [ ] **Hats / P&Ls** — the buckets a task can belong to. Default: `Client delivery` · `Internal product (named)` · `Business-building`.
- [ ] **Delegation roster** — who/what receives work, and each one's strength: human team, AI agents/automation, contractors.

Tip: keep a short standing context block in your repo or rebalance-OS so you
don't re-supply Rocks and roster every morning.

---

## Tuning the one real knob: WIP caps

Default daily caps (stated in every run, adjustable on request):

- **1 protected Rock block** (90 min), scheduled before client work.
- **≤3 client commitments** due today / under SLA.
- **1 batch of quick To-Dos** (<15 min each).

Everything else is Eliminated, Delegated, or parked under **Parked — not today**.

Too tight and you'll fight it daily; too loose and the cap does nothing. Tune it
against a few real days:

- [ ] Run it on an actual dump for 3–5 days.
- [ ] If you routinely blow past the caps on legitimate work, raise them by one.
- [ ] If "Parked — not today" is always empty, the caps are too loose — tighten.

---

## What it deliberately won't do

- **Solve Issues on the spot.** Parking friction so it doesn't detonate the day *is* the value. IDS them weekly.
- **Relabel to feel productive.** A To-Do isn't a Rock; a Rock you're avoiding isn't an Issue.
- **Fake-delegate.** "Defer" is not delegation — every handoff names a person, agent, or contractor with a one-line brief.
- **Write or execute the tasks.** Triage and day-planning only.

---

## Framework & attribution

Based on EOS — the Entrepreneurial Operating System — from *Traction: Get a Grip
on Your Business* by Gino Wickman. EOS®, Rocks, Level 10 Meeting™, and IDS™ are
concepts from that body of work; this skill adapts them for daily, multi-P&L
agency triage, which classic EOS does not cover.
