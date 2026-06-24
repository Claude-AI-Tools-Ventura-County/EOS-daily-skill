---
name: traction-triage
description: >-
  Break down, analyze, and triage a daily task dump for a design/development
  boutique agency using EOS (the Entrepreneurial Operating System from the book
  Traction by Gino Wickman). Use this whenever the user pastes a brain-dump,
  to-do list, inbox, or "here's everything on my plate today" and wants it
  sorted, prioritized, or made sane — even if they don't say "EOS" or
  "Traction." Trigger on phrases like "triage my day," "what should I work on,"
  "I'm drowning in tasks," "sort my to-do list," "plan my day," "too much on my
  plate," or any request to turn a messy list of work into a prioritized plan.
  The skill maps every task to one of five EOS fates (Rock, To-Do, Issue,
  Delegate, Eliminate), protects priority time from billable fires, and flags
  recurring work to systematize. Do NOT use it for writing the tasks themselves
  or for executing them, for building a project roadmap or scheduling future
  milestones, or for generating a brand-new task list from scratch — only for
  triaging an existing dump and planning the day.
---

# Traction Triage

Turn a raw daily task dump into a sane, prioritized, EOS-aligned day plan for a
boutique design/dev agency that runs **client delivery + internal products +
business-building** at the same time.

## Why this skill exists (read once)

EOS has **no daily layer by design**. Its cadences are quarterly (**Rocks**) and
weekly (**Level 10 meeting**, **Scorecard**, **7-day To-Dos**). A daily dump is
not an EOS object. So the entire job here is the **bridge**: force every task to
resolve to exactly one of five EOS fates, then assemble a day that protects what
matters. If a task doesn't get a fate, it's noise dressed as work.

The five fates:

- **Eliminate** — kill it; advances nothing.
- **Delegate** — someone/something else should own it (team, AI agent, contractor).
- **Rock work** — advances a 90-day priority. Protect this time first.
- **To-Do** — concrete, single-owner, doable inside 7 days.
- **Issue** — needs a decision/discussion or has no clear solution. Park it; solve weekly via **IDS** (Identify, Discuss, Solve). Do **not** solve reactively today.

---

## Step 0 — Load context (don't skip)

EOS is only partially in place here, so accept what exists and infer the rest.
Ask for these only if not already known from the conversation or prior context:

- **Current Rocks** (this quarter's 3–7 priorities). If none exist, infer 1–3
  "north-star" priorities from the active product lines and treat them as
  provisional Rocks, and say so.
- **Active hats / P&Ls** — the buckets a task can belong to. Default set:
  `Client delivery` · `Internal product (name it)` · `Business-building`.
- **Delegation roster** — who/what can receive work. Default: human team,
  AI agents/automation, contractors. Note each one's strength so handoffs route
  correctly.

If the user just wants triage and won't supply context, proceed with provisional
Rocks and flag every assumption inline.

---

## Step 1 — Capture

Take the dump exactly as given. Split run-on items into atomic tasks (one
clear next action each). Don't invent tasks. Don't drop any — every input line
must surface in the output with a fate.

---

## Step 2 — Triage cascade (run in this order, per task)

Order matters: the cheapest wins come first (killing and offloading work before
scheduling it). Ask these in sequence and stop at the first that fits.

1. **Eliminate?** Does it advance a Rock, honor a client commitment, or keep the
   business running? If **no to all three**, split by future value: **Eliminate**
   if it has none (kill it), or **Park** as "someday/maybe" (under *Parked — not
   today*) if it has potential value but no current alignment or capacity. Most
   dumps hide 10–20% pure noise here.
2. **Delegate?** Run **Delegate & Elevate** — which quadrant is this task in for
   the user?
   - *Love / Great at it* → keep (this is unique-genius work).
   - *Like / Good at it* → keep for now, candidate to offload later.
   - *Don't like / Good at it* → **Delegate**.
   - *Don't like / Not good at it* → **Delegate immediately.**
   Default bias: anything **outside** the *Love / Great* quadrant (the user's
   unique ability) is a delegation candidate — keep it only when a real
   constraint (no one else can do it, or it's genuinely faster to keep) applies.
   Route each delegated task to a roster target: **team member**, **AI
   agent/automation**, or **contractor** — pick by strength, and write the
   handoff so it's actionable, not just "someone else."
3. **Rock, To-Do, or Issue?** For what remains and genuinely needs the user:
   - Advances a current Rock → **Rock work** → goes in a protected deep-work block.
   - Concrete, single owner, clear next action, doable ≤7 days → **To-Do**.
   - Needs a decision/discussion, has no clear solution, or is recurring friction
     → **Issue** → park on the Issues List for the next L10. Resist solving it now.

---

## Step 3 — Tag every kept task (two axes)

These two tags are what make agency triage work where vanilla EOS fails.

- **Hat / P&L:** `Client` · `Product:<name>` · `Business`. EOS assumes one
  company with one set of Rocks; the user runs several. Without this axis,
  billable fires silently starve the internal-product work where the Rocks
  actually live.
- **$/hour band:** rough `$10` · `$100` · `$1,000`:
  - `$10` — administrative / routine / low-leverage (scheduling, data entry, basic triage).
  - `$100` — specialized execution: client delivery or skilled technical work (design, code, writing).
  - `$1,000` — high-leverage: strategy, business-building, or high-risk calls (architecture, contracts, Rock work).

  Reinforces Delegate & Elevate — anything tagged `$10` that's still assigned to
  the user is a delegation miss; flag it.

---

## Step 4 — Apply WIP caps and assemble the day

EOS keeps Rocks to 3–7 and To-Do lists short on purpose. Enforce a daily cap so
the plan is finishable, not aspirational. Default caps (state them, adjust on request):

- **1 protected Rock block** (90 min) — scheduled *first*, before client work,
  or it never happens.
- **≤3 client commitments** due today / under SLA.
- **≤2 focused To-Dos** (>15 min, internal/business work that is *not* a Rock and
  *not* a client commitment) — the larger non-priority tasks that still need a
  real time block today, so they don't get silently parked.
- **1 batch of quick To-Dos** (<15 min each), done in a single pass.
- Everything else is already Eliminated, Delegated, or parked as an Issue.

**Overflow rule:** anything past the caps is explicitly listed under
**Parked — not today**, not silently dropped. Naming the overflow is the triage.

**Balance check:** if any active P&L — especially `Product` (where Rocks live) —
gets **zero** protected time today, say so plainly. That's the failure mode this
whole skill exists to catch.

---

## Step 5 — Recurring → Process signal

If a task looks like one triaged before (same shape, repeats weekly), don't
re-decide it daily. Flag it for a **Core Process**: "document once, follow by
all." Recurring manual work is a systematizing opportunity, not a daily decision.

**But don't drop today's instance.** A recurring task that is *due today* still
needs a fate in the active plan — schedule, batch, or delegate it now — *in
addition to* the **Systematize** flag. Systematize is about the future process;
it does not complete today's instance. (So a due-today recurring task appears in
both places: once as a today-action, once under Systematize.)

---

## Output format

ALWAYS use this exact structure. Use GitHub-flavored Markdown. Use a checkbox
(`- [ ]`, never bare `[ ]`) ONLY for actions taken *today* — the day plan and the
delegation handoffs you must actually send. Parked work uses plain bullets (`-`):
**Issues**, **Parked**, **Eliminated**, and **Systematize** are not today-actions,
so they never fill the checklist with things you decided *not* to do. Date the
title `YYYY-MM-DD`. Keep it linear and scannable — quick wins read first, deep
work next.

```markdown
# Daily Triage — <YYYY-MM-DD>

## Today's plan (capped)
**Protected Rock block (90 min) — do first**
- [ ] <task>  ·  Rock: <rock>  ·  <Hat/P&L>  ·  $<band>

**Client commitments (≤3)**
- [ ] <task>  ·  <client>  ·  $<band>

**Focused To-Dos (>15 min, internal/business — ≤2)**
- [ ] <task>  ·  <Hat/P&L>  ·  $<band>

**Quick To-Dos (batch, <15 min each)**
- [ ] <task>  ·  <Hat/P&L>
- [ ] <task>  ·  <Hat/P&L>

## Delegated (handed off, not yours today)
- [ ] <task>  →  <team / agent:name / contractor>  ·  <one-line handoff>

## Issues — park for next L10 (IDS, don't solve now)
- <issue, framed as the real problem>

## Parked — not today (over cap / someday)
- <task>  ·  <why parked>

## Eliminated
- <task>  —  <why it advances nothing>

## Systematize (recurring → Core Process)
- <recurring task>  →  document as Core Process

## Balance check
- <one or two lines: which P&L got protected time, which got none, $10 work still on your plate>
```

---

## Worked example (compact, but faithful to the output format)

**Input dump:**
"fix Binoid checkout bug; reply to 14 emails; finally write the Hypercart query-guard
docs (Rock); set up the staging env for the internal dashboard; pick a logo color for
the meetup deck; teammate asked about invoicing; research a new CI tool; same weekly
client status report."

**Output:**

```markdown
# Daily Triage — 2026-06-23

## Today's plan (capped)
**Protected Rock block (90 min) — do first**
- [ ] Write Hypercart query-guard docs  ·  Rock: ship Query Guard  ·  Product:Hypercart  ·  $1,000

**Client commitments (≤3)**
- [ ] Fix Binoid checkout bug  ·  Binoid  ·  $1,000

**Focused To-Dos (>15 min, internal/business — ≤2)**
- [ ] Set up staging env for the internal dashboard  ·  Product:Dashboard  ·  $100

**Quick To-Dos (batch, <15 min each)**
- [ ] Triage 14 emails (single pass)  ·  Business

## Delegated (handed off, not yours today)
- [ ] Pick logo color  →  agent:design-mock  ·  "3 on-brand options for the meetup deck"
- [ ] Answer invoicing question  →  team:ops  ·  "reply + link the SOP"
- [ ] Draft weekly client status report (due today)  →  agent:status-draft  ·  "pull metrics + draft; I review & send"

## Issues — park for next L10 (IDS, don't solve now)
- Which CI tool to adopt — needs a decision, not a today-task

## Parked — not today (over cap / someday)
- (nothing over cap today)

## Eliminated
- (none today)

## Systematize (recurring → Core Process)
- Weekly client status report  →  document as Core Process (template + agent draft)
  *(also delegated above so today's report still ships)*

## Balance check
- Product protected ✔ (Hypercart Rock + dashboard To-Do); Client covered ✔; logo + invoicing
  ($10–$100 work) correctly off your plate. Weekly status report is delegated for *today* **and**
  flagged to systematize — done now, automated next time.
```

---

## EOS fidelity guardrails

- **Don't solve Issues reactively.** The point of the Issues List is to *not*
  let today's friction detonate the day. Park, then IDS weekly.
- **Rocks are quarterly, To-Dos are 7-day, Issues are parked** — never relabel a
  To-Do as a Rock to feel productive, or a Rock as an Issue to avoid it.
- **Delegate needs a real target.** "Defer" is not delegation. Every delegated
  task names a person, an agent, or a contractor, with a one-line handoff.
- **Protect the Rock block first.** In an agency, billable work always feels more
  urgent than the priority work — schedule the Rock block before client tasks or
  it loses every day.
- **Use canonical EOS terms** (Rock, To-Do, Issue, IDS, L10, Scorecard, Delegate
  & Elevate, Core Process) so the output stays legible to anyone who knows the book.
