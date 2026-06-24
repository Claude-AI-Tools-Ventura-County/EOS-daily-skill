# Relay — Improve `SKILL.md` (traction-triage)

STATUS: Approved
NEXT: None

- **Token:** `RELAY-SKILL` (tick, in the harness clone)
- **Producer:** `claude-producer` (applies fixes to the artifact)
- **Reviewer:** `agy` (Antigravity CLI — critiques, proposes fixes, does NOT edit the artifact)
- **TARGET (artifact under review):** `SKILL.md` — the `traction-triage` skill, an EOS-based
  daily task-triage skill for a boutique design/dev agency.
- **Goal:** Make `SKILL.md` a tighter, more correct, more usable skill. Improve clarity,
  trigger precision, EOS fidelity, the triage cascade, and the output contract — without
  bloating it or breaking the existing structure.

---

## ▶ TAKE YOUR TURN

You are taking one turn in a turn-based relay. Act ONLY for the role named by the `NEXT:`
header line at the top of this file. Use the **absolute, env-pinned** `tick` for every token
op (a bare `tick`/`./bin/tick` from a worktree silently no-ops and deadlocks the relay).

### If `NEXT: Reviewer` (you are `agy`) — REVIEW, do not edit the artifact

1. Claim the token FIRST (the `--paths` flag is mandatory):
   `tick claim RELAY-SKILL --agent agy --paths relay-system/2026-06-23/skill-md-improve.md`
2. Read the **TARGET** file `SKILL.md` (relative to your current working directory — it is
   present in your checkout). Read the previous Producer turn below, if any.
3. Evaluate `SKILL.md` against these criteria and find the highest-value improvements:
   - **Trigger precision** — does the `description` fire on the right requests and *not*
     over/under-trigger? Are the negative cases ("do NOT use") right?
   - **EOS fidelity** — are Rock / To-Do / Issue / IDS / L10 / Delegate & Elevate / Core
     Process used correctly and consistently with the book *Traction*?
   - **Triage cascade** — is the Step-2 order sound (Eliminate → Delegate → Rock/To-Do/Issue)?
     Any logical gaps, double-counting, or fates a task could fall between?
   - **Usability** — is the output contract unambiguous and copy-pasteable? Is anything
     underspecified (date handling, missing context, empty sections)?
   - **Concision** — any redundancy, bloat, or contradiction to cut? Don't pad.
4. **Append** a Reviewer block (template below) to THIS file. Grade each finding
   `[blocker] / [major] / [minor] / [nit]` with a concrete, actionable fix. If you believe
   the artifact is already excellent and no material improvement remains, say so explicitly.
5. Decide and hand off:
   - **More improvements warranted:** set the header `NEXT: Producer`, then
     `tick release RELAY-SKILL --agent agy --to claude-producer`.
   - **Approve (no material improvement left):** set the header `STATUS: Approved`, then
     `tick done RELAY-SKILL`.
6. Do NOT edit `SKILL.md` or any file other than this relay file. Do NOT run git.

### If `NEXT: Producer` (you are `claude-producer`) — APPLY fixes

1. `tick claim RELAY-SKILL --agent claude-producer --paths SKILL.md`
2. Read the latest Reviewer block. Apply the findings worth applying to `SKILL.md`.
3. Append a Producer block (template below): what you changed, what you deferred and why.
4. Set the header `NEXT: Reviewer`. Commit `SKILL.md` + this file.
5. `tick release RELAY-SKILL --agent claude-producer --to agy`.

---

## Turn log (append below; newest at the bottom)

### Producer turn 0 — seed (claude-producer)

Artifact `SKILL.md` exists and is committed. Handing the first turn to the Reviewer (`agy`)
for an initial critique. No changes yet.

<!-- Reviewer/Producer turns are appended below this line -->

### Reviewer turn 1 — Critique (agy)

I have evaluated `SKILL.md` against trigger precision, EOS fidelity, triage cascade, usability, and concision. Here are the graded findings and actionable fixes:

- **[major] Structural / Triage Gap:**
  - *Finding:* Under the current WIP caps and Output format, there is no place in "Today's plan" for important operational, internal, or business-building To-Dos that are NOT Rock work, NOT client commitments, and take more than 15 minutes (e.g., a 1-hour task to write internal documentation or set up an internal environment). These tasks would be forced to be parked incorrectly or miscategorized.
  - *Fix:* In Step 4 (WIP caps) and the Output format, add a category/cap for general internal/business To-Dos (e.g., `**Daily To-Dos (internal/business, ≤2)**`), or explicitly define how non-quick, non-client To-Dos should be triaged (e.g., categorized under general To-Dos with a separate WIP cap).

- **[major] Output Format Contradiction (Delegation):**
  - *Finding:* The Output format template specifies checkboxes `- [ ]` for Delegated items (line 157), but the Worked example uses simple bullet points without checkboxes (lines 190-191).
  - *Fix:* Align the template and the worked example. Remove checkboxes from the `## Delegated` section in the template and use simple bullet points `- ` or `- Delegated: ` since delegated tasks are "not yours today" and shouldn't clutter the user's active checkbox list.

- **[minor] Usability / Checkbox Noise:**
  - *Finding:* Sections like `## Issues` (parked for the weekly L10) and `## Parked` (not today) use checkboxes (`- [ ]`), which creates noise and confusion in the daily plan. A user copying their plan into a checklist tool will have active checkboxes for tasks they decided not to do today.
  - *Fix:* Remove checkboxes `- [ ]` from `## Issues` and `## Parked` sections in the template and worked example, converting them to plain list bullets (`- `).

- **[minor] Trigger Precision / Negative Cases:**
  - *Finding:* The frontmatter description could trigger on requests to write project roadmaps, create new task checklists from scratch, or schedule future project milestones (which the skill is not meant to execute).
  - *Fix:* Add explicit negative trigger instructions in the frontmatter description: "Do NOT use for project roadmap planning, creating new task lists/checklists from scratch (e.g. project breakdown), or scheduling future milestones."

- **[nit] Date Formatting Ambiguity:**
  - *Finding:* The `# Daily Triage — <date>` title placeholder is underspecified.
  - *Fix:* Suggest a preferred standard format like `YYYY-MM-DD` or `Month DD, YYYY` to guide the model.

- **[nit] Delegate & Elevate Clarity:**
  - *Finding:* Step 2 lists four mappings based on EOS Delegate & Elevate, but doesn't explicitly describe handling tasks that don't fit typical day-to-day categories, or what to do if the user's skillset changes.
  - *Fix:* Clarify that tasks outside the user's "unique ability" (Love/Great) should be systematically targeted for delegation.

### Producer turn 1 — Applied (claude-producer)

All six findings were actionable. Applied:

- **[major] Triage gap** — APPLIED. Added a **Focused To-Dos (>15 min, internal/business — ≤2)**
  category to both Step 4 (WIP caps) and the Output format template, for the larger non-Rock,
  non-client tasks that previously had no home and got silently parked. Used "Focused To-Dos"
  rather than "Daily To-Dos" so the name signals *size/effort* (a real time block) vs the
  existing "Quick To-Dos" batch.
- **[major] Delegation checkbox contradiction** — APPLIED, with a deliberate variation on the
  proposed direction. Rather than *removing* the Delegated checkbox, I kept it and rewrote the
  worked example to match the template. Rationale: a handoff **is** an action you take today
  ("send the brief to X"), so a checkbox you tick once it's actually handed off is correct and
  consistent with the skill's "checkbox = today-action" rule. I made that rule explicit (below)
  so the boundary is principled, not ad hoc.
- **[minor] Checkbox noise** — APPLIED, generalized. Stripped checkboxes from **Issues**,
  **Parked**, **Eliminated** (already plain), AND **Systematize** — none are today-actions.
  Added a one-paragraph rule to the Output format intro: checkboxes only for *today-actions*
  (day plan + delegation handoffs); parked work uses plain bullets.
- **[minor] Trigger negative cases** — APPLIED. Extended the frontmatter `Do NOT use` clause to
  exclude roadmap/milestone planning and generating a task list from scratch.
- **[nit] Date format** — APPLIED. Template title is now `# Daily Triage — <YYYY-MM-DD>` and the
  intro states the `YYYY-MM-DD` convention; the worked example uses a concrete date.
- **[nit] Delegate & Elevate clarity** — APPLIED. Added a "default bias" line: anything outside
  the *Love / Great* (unique-ability) quadrant is a delegation candidate unless a real
  constraint justifies keeping it.

The one place I diverged from the literal suggestion is the Delegated checkbox (kept, not
removed) — flagging it explicitly for your re-review. Handing back for verification.

### Reviewer turn 2 — Critique (agy)

I have verified the Producer's changes and evaluated the updated `SKILL.md`. While the changes (including retaining the `Delegated` checkbox for active handoffs) are excellent, I found a few remaining logical and execution gaps:

- **[major] Execution Gap (Recurring Tasks):**
  - *Finding:* In the worked example, the task `"same weekly client status report"` is triaged to `## Systematize`, but it is completely omitted from the actual day plan (`## Today's plan` or `## Delegated`). Since this is a recurring commitment due today, omitting it from execution means the task is dropped and the report won't be completed. Recurring tasks that are due today must still be executed (or delegated) *today*, in addition to being flagged for future systematization.
  - *Fix:* Clarify in Step 5 and the Output format that recurring tasks must *both* be scheduled/delegated in today's active plan (if they are due today) *and* listed under `## Systematize`. Update the worked example to include the status report in client commitments (or delegated) as well as under `## Systematize`.

- **[minor] Tagging Guidelines for $/hour Bands:**
  - *Finding:* Step 3 introduces the `$10` / `$100` / `$1,000` bands but doesn't define the criteria for assigning them, leaving the model to guess or apply them inconsistently.
  - *Fix:* Add brief definitions for each band in Step 3. For example:
    - `$10`: Administrative, routine, or low-leverage tasks (e.g., scheduling, data entry, basic triage).
    - `$100`: Specialized execution, client delivery, or skilled technical tasks (e.g., design, coding, standard writing).
    - `$1,000`: High-leverage strategic, business-building, or high-risk tasks (e.g., architectural decisions, client contract negotiation, Rock work).

- **[minor] Triage Ambiguity ("Someday/Maybe" vs. Eliminate):**
  - *Finding:* Step 2, Rule 1 says: "If no to all three -> Eliminate (or park as 'someday/maybe')". However, "someday/maybe" tasks belong in `## Parked — not today (over cap / someday)`, whereas truly useless tasks belong in `## Eliminated`. The current phrasing mixes these, which could lead the model to put someday/maybe tasks in `## Eliminated` or vice-versa.
  - *Fix:* Clarify Step 2, Rule 1 to distinguish the two fates: "If no to all three, either **Eliminate** (if it has zero future value) or **Park** (under `## Parked` as 'someday/maybe' if it has potential future value but no current alignment/capacity)."

### Producer turn 2 — Applied (claude-producer)

All three round-2 findings applied:

- **[major] Recurring task execution gap** — APPLIED. This was the sharpest catch. Step 5 now
  states that a recurring task *due today* needs a fate in the active plan **and** a Systematize
  flag — Systematize is about the future process, not today's instance. Updated the worked
  example: the weekly status report is now **delegated for today** (`agent:status-draft`) and
  still listed under Systematize, with the balance check noting "done now, automated next time."
- **[minor] $/hour band criteria** — APPLIED. Step 3 now defines each band ($10 admin/routine,
  $100 specialized execution / client delivery, $1,000 high-leverage strategy / Rock work),
  roughly per your examples.
- **[minor] Someday/Maybe vs Eliminate** — APPLIED. Step 2 Rule 1 now splits the "no to all
  three" case explicitly: **Eliminate** (zero future value) vs **Park** under *Parked* (potential
  value, no current alignment/capacity).

No divergences this round. Handing back for verification.

### Reviewer turn 3 — Critique (agy)

I have evaluated the updated `SKILL.md` against trigger precision, EOS fidelity, triage cascade, usability, and concision. While the round-2 fixes are correctly implemented, I have identified a few remaining logical and execution gaps for final resolution:

- **[major] Capacity / SLA Conflict on Client Commitments:**
  - *Finding:* Step 4 enforces a hard daily WIP cap of `≤3` on client commitments due today / under SLA. If a user has 5 client commitments due today that cannot be delegated, the overflow rule dictates listing them under `## Parked — not today`. In a boutique agency, parking SLA-bound commitments means breaching SLAs or missing critical deadlines.
  - *Fix:* Clarify in Step 4 that client commitments due today that exceed the cap must either be delegated, rescheduled/renegotiated with the client (and then parked), or, if they must be executed by the user today, they must be included in the active plan and flagged in the Balance Check as a capacity overload (with a recommendation to add "Capacity constraint / hiring need" to the L10 Issues list).

- **[minor] Handling Empty Rock Block:**
  - *Finding:* If a user's daily dump contains zero tasks related to their Rocks, the model cannot invent tasks (per Step 1) but the output template has a mandatory `Protected Rock block` section. It is not explicitly stated how the model should format this section when empty.
  - *Fix:* Clarify in Step 4 and the Output format that if no Rock work is present in the task dump, the Protected Rock block should be listed as `- (None - no Rock tasks identified in today's dump)` and the Balance Check must flag this as a critical warning (e.g., "WARNING: Product P&L / Rocks got zero time today. Your strategic growth is stalled.").

- **[minor] Structured Balance Check Output:**
  - *Finding:* The `## Balance check` section in the template is currently free-form (`- <one or two lines: ...>`), which may lead to vague or inconsistent summaries. Since its primary purpose is to catch two critical failure modes (starved P&Ls / Rocks, and undelegated $10 work), a structured format would guarantee these checks are always performed and are immediately scannable.
  - *Fix:* Specify a structured template for the balance check in the Output format, such as:
    ```markdown
    ## Balance check
    - **P&L Status:** <e.g., Product: Protected (90m) · Client: Covered · Business: Starved (0m)>
    - **Delegation Misses:** <e.g., None · OR Warning: 1 kept $10 task (<task>)>
    ```
    Update the worked example to match this structured format.

- **[minor] Missing Cap / Limits on Quick To-Dos:**
  - *Finding:* Step 4 specifies a cap of "1 batch of quick To-Dos (<15 min each)", but does not limit the number of items allowed in this batch. If a dump has 10 "quick" tasks, placing them all in the batch would take up to 150 minutes, defeating the purpose of a quick pass and overloading the day.
  - *Fix:* Define a clear cap on the number of items or total duration for the quick To-Dos batch (e.g., `≤4 items` or `≤30 minutes total time`).

- **[minor] Inconsistent $/hour Banding in Worked Example:**
  - *Finding:* In the worked example, the task `"Fix Binoid checkout bug"` (coding/debugging client delivery) is tagged `$1,000`. However, Step 3 defines `$100` as "specialized execution: client delivery or skilled technical work (design, code, writing)" and `$1,000` as "high-leverage: strategy, business-building, or high-risk calls". General debugging falls under specialized execution ($100), not high-leverage strategy ($1,000), making the worked example contradict the definitions in Step 3.
  - *Fix:* Change the tag of the Binoid checkout bug task in the worked example to `$100` to align with the definitions, or clarify in Step 3 that client fires/blockers that directly halt client revenue can be elevated to `$1,000` due to their high-risk/high-impact nature.

- **[minor] Tagging Inconsistency for Client Commitments:**
  - *Finding:* Step 3 defines the Hat / P&L tag for client work as `Client`. However, the Output format template uses `<client>` (line 174) and the worked example uses `Binoid` (line 222) in place of the `<Hat/P&L>` tag.
  - *Fix:* Align the naming convention. Specify in Step 3 and the template that the client tag should be formatted as `Client:<Client Name>` (e.g., `Client:Binoid`), mirroring the `Product:<name>` style. This makes the P&L tags consistent across all sections.

### Producer turn 3 — Applied (claude-producer)

All six round-3 findings applied:

- **[major] Capacity / SLA conflict** — APPLIED. Step 4 now carries an **SLA exception** to the
  ≤3 client-commitment cap: SLA-bound commitments that exceed the cap and can't be delegated are
  *not* parked (which would breach the SLA) — they stay in the active plan, the overload is flagged
  in the Balance check, and "Capacity constraint / hiring need" goes onto the Issues list for L10.
- **[minor] Empty Rock block** — APPLIED. Step 4 now says: if the dump has no Rock work, render the
  block as `- (none — no Rock tasks in today's dump)` and raise a critical flag in the Balance check.
- **[minor] Structured Balance check** — APPLIED. Replaced the free-form balance line with a
  structured block (**P&L status / Rocks / Delegation misses / Capacity**) in both the template and
  the worked example, so the two core failure modes (starved Rocks, undelegated $10 work) — plus the
  new SLA-overload check — are always performed and scannable.
- **[minor] Quick To-Dos cap** — APPLIED. The batch is now capped at **≤30 min total** (Step 4 +
  both section headers), so a pile of "quick" tasks can't quietly consume the day.
- **[minor] $/band inconsistency (Binoid)** — APPLIED via the clarify option. Step 3's `$1,000`
  definition now notes a client fire that *halts revenue* can rate `$1,000` by impact even if the
  task is routine execution — so the revenue-halting checkout bug legitimately stays `$1,000`.
- **[minor] Client tag consistency** — APPLIED. Standardized the P&L tag to `Client:<name>`
  (mirroring `Product:<name>`) in Step 3, the template, and the worked example (`Client:Binoid`).

I believe the skill is now materially complete and internally consistent. Handing back: please
approve if no material improvement remains, per your turn instructions.

### Reviewer turn 4 — Critique (agy)

I have evaluated the updated `SKILL.md` against trigger precision, EOS fidelity, triage cascade, usability, and concision. The round-3 fixes have been applied correctly and thoroughly. I find no remaining material improvements or gaps in the skill. It is fully aligned with EOS principles, internally consistent, clear, and highly usable.

Therefore, I approve this version of the skill.
