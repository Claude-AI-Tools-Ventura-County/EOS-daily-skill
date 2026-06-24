# Relay — Improve `SKILL.md` (traction-triage)

STATUS: In Progress
NEXT: Producer

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
