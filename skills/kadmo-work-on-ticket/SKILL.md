---
name: kadmo-work-on-ticket
description: Run a Kadmo playbook on one tracker ticket and follow the run to its result. Use when someone asks Kadmo's agents to fix, implement or check a ticket, or asks how a ticket's run is going.
---

# Work on a ticket with Kadmo

This skill uses the `kadmo` MCP server's tools.

1. **Check the account.** `whoami` names the account and role the session acts for. Say which account it is if the person may have more than one.
2. **Pick the playbook.** `list_playbooks` returns the catalog with exact slugs. `work_on_task` matches a slug exactly, so `bug-fix-copy` and `bug-fix` are different playbooks. `get_issue_type_routing` shows which playbook a ticket's issue type starts by default.
3. **Check the ticket is not already running.** `get_task` shows its runs and the controls that apply now. A new run is not needed for a run that is paused: after an operator's pause, `control_task` with `action: "resume"` carries on. At a gate halt the other actions change the outcome (`override` passes the gate, `rerun` discards steps, `done` and `cancel` end the run), so ask the person which one they want.
4. **Start it.** Confirm the ticket, the playbook and any effort tier with the person, because a run can spend the account's credit. Then call `work_on_task` with `ticket`, `playbook`, `effort` if the person chose a tier, and `hint` if they gave extra context. The hint goes to the agent on every step of the run.
5. **Follow it.** `get_task` shows the run's status and steps. `get_run_transcript` shows what the agent did in a job, in summary or in full.
6. **Report.** Give the person the result, the evidence the run left and any step that needs a decision. `review_tasks` lists everything in the pool that needs action.

If the ticket has blockers, the scheduler holds the run until they clear: say so instead of starting it again.
