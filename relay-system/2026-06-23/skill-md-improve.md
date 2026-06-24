# Relay — Improve `SKILL.md` (traction-triage)

STATUS: In Progress
NEXT: Reviewer

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
