# Changelog

All notable changes to the **traction-triage** skill are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased]

### Skill review — `SKILL.md` (2026-06-23)

Reworked `SKILL.md` via an automated producer↔reviewer relay with **agy (Antigravity
CLI)** as the reviewer (4 review rounds, 15 graded findings, approved). Net: **+104 / −37**.
Full audit trail: [`relay-system/2026-06-23/skill-md-improve.md`](relay-system/2026-06-23/skill-md-improve.md).

#### Added
- **"Focused To-Dos" category** (>15 min, internal/business, *not* a Rock or client
  commitment), capped at ≤2 — closes a triage gap where larger non-priority tasks had
  no home and got silently parked. Added to the WIP caps (Step 4) and the output template.
- **`$/hour` band definitions** — `$10` (admin/routine), `$100` (specialized execution /
  client delivery), `$1,000` (high-leverage strategy / Rock work), with a note that a
  client fire that *halts revenue* can rate `$1,000` by impact.
- **SLA exception** to the `≤3` client-commitment cap: SLA-bound commitments over the cap
  are kept in the active plan (never silently parked), the overload is flagged in the
  Balance check, and "Capacity constraint / hiring need" is added to the L10 Issues list.
- **Empty Rock-block handling** — if the dump has no Rock work, render the block as
  `- (none …)` and raise a critical Balance-check warning that strategic work is stalled.
- **Structured Balance check** — replaced the free-form line with **P&L status / Rocks /
  Delegation misses / Capacity** so the core failure modes are always checked and scannable.
- **Recurring-task dual-fate rule** (Step 5) — a recurring task *due today* must get a fate
  in the active plan **and** a Systematize flag; Systematize alone does not complete today.
- **Delegation "default bias"** — anything outside the *Love / Great* (unique-ability)
  quadrant is a delegation candidate unless a real constraint justifies keeping it.
- **Quick To-Dos cap** — the batch is now bounded to ≤30 min total.

#### Changed
- **Checkbox policy** — checkboxes (`- [ ]`) are now reserved for *today-actions* (the day
  plan and delegation handoffs); **Issues**, **Parked**, **Eliminated**, and **Systematize**
  use plain bullets so the checklist never fills with things you decided *not* to do today.
- **P&L tag standardized** to `Client:<name>`, mirroring `Product:<name>`.
- **Date format** pinned to `YYYY-MM-DD` in the output template.
- **Trigger precision** — the `description` now explicitly excludes roadmap/milestone
  planning and generating task lists from scratch.
- **Worked example** rewritten as a compact but faithful instance of the output format
  (replacing the loose "excerpt"), demonstrating the new sections and conventions.

#### Fixed
- **Template ↔ worked-example checkbox inconsistency** in the Delegated section.
- **`$/hour` banding contradiction** — the revenue-halting Binoid checkout fire is now
  consistent with the band definitions (`$1,000` by impact).

<details>
<summary>Full diff — <code>SKILL.md</code> (+104 / −37)</summary>

````diff
diff --git a/SKILL.md b/SKILL.md
index f4ba629..b3e8588 100644
--- a/SKILL.md
+++ b/SKILL.md
@@ -12,7 +12,9 @@ description: >-
   The skill maps every task to one of five EOS fates (Rock, To-Do, Issue,
   Delegate, Eliminate), protects priority time from billable fires, and flags
   recurring work to systematize. Do NOT use it for writing the tasks themselves
-  or for executing them — only for triage and day-planning.
+  or for executing them, for building a project roadmap or scheduling future
+  milestones, or for generating a brand-new task list from scratch — only for
+  triaging an existing dump and planning the day.
 ---
 
 # Traction Triage
@@ -72,14 +74,19 @@ Order matters: the cheapest wins come first (killing and offloading work before
 scheduling it). Ask these in sequence and stop at the first that fits.
 
 1. **Eliminate?** Does it advance a Rock, honor a client commitment, or keep the
-   business running? If **no to all three** → **Eliminate** (or park as
-   "someday/maybe"). Most dumps hide 10–20% pure noise here.
+   business running? If **no to all three**, split by future value: **Eliminate**
+   if it has none (kill it), or **Park** as "someday/maybe" (under *Parked — not
+   today*) if it has potential value but no current alignment or capacity. Most
+   dumps hide 10–20% pure noise here.
 2. **Delegate?** Run **Delegate & Elevate** — which quadrant is this task in for
    the user?
    - *Love / Great at it* → keep (this is unique-genius work).
    - *Like / Good at it* → keep for now, candidate to offload later.
    - *Don't like / Good at it* → **Delegate**.
    - *Don't like / Not good at it* → **Delegate immediately.**
+   Default bias: anything **outside** the *Love / Great* quadrant (the user's
+   unique ability) is a delegation candidate — keep it only when a real
+   constraint (no one else can do it, or it's genuinely faster to keep) applies.
    Route each delegated task to a roster target: **team member**, **AI
    agent/automation**, or **contractor** — pick by strength, and write the
    handoff so it's actionable, not just "someone else."
@@ -95,13 +102,17 @@ scheduling it). Ask these in sequence and stop at the first that fits.
 
 These two tags are what make agency triage work where vanilla EOS fails.
 
-- **Hat / P&L:** `Client` · `Product:<name>` · `Business`. EOS assumes one
+- **Hat / P&L:** `Client:<name>` · `Product:<name>` · `Business`. EOS assumes one
   company with one set of Rocks; the user runs several. Without this axis,
   billable fires silently starve the internal-product work where the Rocks
   actually live.
-- **$/hour band:** rough `$10` · `$100` · `$1,000`. Reinforces Delegate &
-  Elevate — anything tagged `$10` that's still assigned to the user is a
-  delegation miss; flag it.
+- **$/hour band:** rough `$10` · `$100` · `$1,000`:
+  - `$10` — administrative / routine / low-leverage (scheduling, data entry, basic triage).
+  - `$100` — specialized execution: client delivery or skilled technical work (design, code, writing).
+  - `$1,000` — high-leverage: strategy, business-building, or high-risk calls (architecture, contracts, Rock work). A client fire that directly halts revenue can also rate `$1,000` by *impact*, even when the task itself is routine execution.
+
+  Reinforces Delegate & Elevate — anything tagged `$10` that's still assigned to
+  the user is a delegation miss; flag it.
 
 ---
 
@@ -111,9 +122,19 @@ EOS keeps Rocks to 3–7 and To-Do lists short on purpose. Enforce a daily cap s
 the plan is finishable, not aspirational. Default caps (state them, adjust on request):
 
 - **1 protected Rock block** (90 min) — scheduled *first*, before client work,
-  or it never happens.
-- **≤3 client commitments** due today / under SLA.
-- **1 batch of quick To-Dos** (<15 min each), done in a single pass.
+  or it never happens. If the dump has **no** Rock work, don't invent it: render
+  the block as `- (none — no Rock tasks in today's dump)` and raise a critical
+  flag in the Balance check — strategic work is stalled.
+- **≤3 client commitments** due today / under SLA. **SLA exception:** if more than
+  3 are genuinely due today and can't be delegated, do *not* silently park them
+  (that breaches the SLA) — keep them in the active plan, flag the overload in the
+  Balance check, and add "Capacity constraint / hiring need" to the Issues list
+  for the next L10. Renegotiate or reschedule with the client where you can.
+- **≤2 focused To-Dos** (>15 min, internal/business work that is *not* a Rock and
+  *not* a client commitment) — the larger non-priority tasks that still need a
+  real time block today, so they don't get silently parked.
+- **1 batch of quick To-Dos** (<15 min each, **≤30 min total** for the batch),
+  done in a single pass.
 - Everything else is already Eliminated, Delegated, or parked as an Issue.
 
 **Overflow rule:** anything past the caps is explicitly listed under
@@ -131,25 +152,38 @@ If a task looks like one triaged before (same shape, repeats weekly), don't
 re-decide it daily. Flag it for a **Core Process**: "document once, follow by
 all." Recurring manual work is a systematizing opportunity, not a daily decision.
 
+**But don't drop today's instance.** A recurring task that is *due today* still
+needs a fate in the active plan — schedule, batch, or delegate it now — *in
+addition to* the **Systematize** flag. Systematize is about the future process;
+it does not complete today's instance. (So a due-today recurring task appears in
+both places: once as a today-action, once under Systematize.)
+
 ---
 
 ## Output format
 
-ALWAYS use this exact structure. Use GitHub-flavored Markdown. Every actionable
-line is a checkbox with a hyphen prefix: `- [ ]` (never bare `[ ]`). Keep it
-linear and scannable — quick wins (kills, handoffs) read first, deep work next.
+ALWAYS use this exact structure. Use GitHub-flavored Markdown. Use a checkbox
+(`- [ ]`, never bare `[ ]`) ONLY for actions taken *today* — the day plan and the
+delegation handoffs you must actually send. Parked work uses plain bullets (`-`):
+**Issues**, **Parked**, **Eliminated**, and **Systematize** are not today-actions,
+so they never fill the checklist with things you decided *not* to do. Date the
+title `YYYY-MM-DD`. Keep it linear and scannable — quick wins read first, deep
+work next.
 
 ```markdown
-# Daily Triage — <date>
+# Daily Triage — <YYYY-MM-DD>
 
 ## Today's plan (capped)
 **Protected Rock block (90 min) — do first**
 - [ ] <task>  ·  Rock: <rock>  ·  <Hat/P&L>  ·  $<band>
 
 **Client commitments (≤3)**
-- [ ] <task>  ·  <client>  ·  $<band>
+- [ ] <task>  ·  Client:<name>  ·  $<band>
 
-**Quick To-Dos (batch, <15 min each)**
+**Focused To-Dos (>15 min, internal/business — ≤2)**
+- [ ] <task>  ·  <Hat/P&L>  ·  $<band>
+
+**Quick To-Dos (batch, <15 min each, ≤30 min total)**
 - [ ] <task>  ·  <Hat/P&L>
 - [ ] <task>  ·  <Hat/P&L>
 
@@ -157,43 +191,76 @@ linear and scannable — quick wins (kills, handoffs) read first, deep work next
 - [ ] <task>  →  <team / agent:name / contractor>  ·  <one-line handoff>
 
 ## Issues — park for next L10 (IDS, don't solve now)
-- [ ] <issue, framed as the real problem>
+- <issue, framed as the real problem>
 
 ## Parked — not today (over cap / someday)
-- [ ] <task>  ·  <why parked>
+- <task>  ·  <why parked>
 
 ## Eliminated
 - <task>  —  <why it advances nothing>
 
 ## Systematize (recurring → Core Process)
-- [ ] <recurring task>  →  document as Core Process
+- <recurring task>  →  document as Core Process
 
 ## Balance check
-- <one or two lines: which P&L got protected time, which got none, $10 work still on your plate>
+- **P&L status:** <e.g., Product: protected (90m) · Client: covered · Business: starved (0m)>
+- **Rocks:** <e.g., 1 Rock block protected · OR ⚠ no Rock time today — strategic work stalled>
+- **Delegation misses:** <e.g., none · OR ⚠ 1 kept $10 task: <task>>
+- **Capacity:** <e.g., within caps · OR ⚠ SLA overload: N client commitments over the cap>
 ```
 
 ---
 
-## Worked example (abbreviated)
+## Worked example (compact, but faithful to the output format)
 
 **Input dump:**
 "fix Binoid checkout bug; reply to 14 emails; finally write the Hypercart query-guard
-docs (Rock); pick a logo color for the meetup deck; teammate asked about invoicing;
-research new CI tool; same weekly client status report."
-
-**Output (excerpt):**
-
-- Protected Rock block: write Hypercart query-guard docs · Rock: ship Query Guard ·
-  Product:Hypercart · $1,000
-- Client commitments: fix Binoid checkout bug · Binoid · $1,000
-- Quick To-Dos: triage 14 emails (batch, 15 min)
-- Delegated: pick logo color → agent:design-mock or teammate · "3 options, on-brand palette"
-- Delegated: invoicing question → team:ops · "answer + link the SOP"
-- Issues (park for L10): "which CI tool" — needs a decision, not a today-task
-- Eliminated: none today
-- Systematize: weekly client status report → Core Process (template + agent draft)
-- Balance check: Product (Hypercart Rock) protected ✔; Client covered ✔; logo + research
-  were $10–$100 work correctly off your plate.
+docs (Rock); set up the staging env for the internal dashboard; pick a logo color for
+the meetup deck; teammate asked about invoicing; research a new CI tool; same weekly
+client status report."
+
+**Output:**
+
+```markdown
+# Daily Triage — 2026-06-23
+
+## Today's plan (capped)
+**Protected Rock block (90 min) — do first**
+- [ ] Write Hypercart query-guard docs  ·  Rock: ship Query Guard  ·  Product:Hypercart  ·  $1,000
+
+**Client commitments (≤3)**
+- [ ] Fix Binoid checkout bug  ·  Client:Binoid  ·  $1,000
+
+**Focused To-Dos (>15 min, internal/business — ≤2)**
+- [ ] Set up staging env for the internal dashboard  ·  Product:Dashboard  ·  $100
+
+**Quick To-Dos (batch, <15 min each, ≤30 min total)**
+- [ ] Triage 14 emails (single pass)  ·  Business
+
+## Delegated (handed off, not yours today)
+- [ ] Pick logo color  →  agent:design-mock  ·  "3 on-brand options for the meetup deck"
+- [ ] Answer invoicing question  →  team:ops  ·  "reply + link the SOP"
+- [ ] Draft weekly client status report (due today)  →  agent:status-draft  ·  "pull metrics + draft; I review & send"
+
+## Issues — park for next L10 (IDS, don't solve now)
+- Which CI tool to adopt — needs a decision, not a today-task
+
+## Parked — not today (over cap / someday)
+- (nothing over cap today)
+
+## Eliminated
+- (none today)
+
+## Systematize (recurring → Core Process)
+- Weekly client status report  →  document as Core Process (template + agent draft)
+  *(also delegated above so today's report still ships)*
+
+## Balance check
+- **P&L status:** Product: protected (Hypercart Rock + dashboard To-Do) · Client: covered · Business: light
+- **Rocks:** 1 Rock block protected ✔
+- **Delegation misses:** none — logo, invoicing, and the status-report draft ($10–$100 work) are all off your plate
+- **Capacity:** within caps ✔ — status report delegated for *today* **and** flagged to systematize (done now, automated next time)
+```
 
 ---
````

</details>
