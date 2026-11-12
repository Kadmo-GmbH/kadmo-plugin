---
name: kadmo-fleet
description: Check Kadmo's agents and dispatch a workflow to one. Use when someone asks which agents are free, what an agent is doing, or wants a named workflow run or queued on an agent.
---

# Kadmo's agent fleet

This skill uses the `kadmo` MCP server's tools.

## See the fleet

- `list_agents`: every agent with its status, roles, workspaces, session count and active job.
- `get_agent_status`: one agent in detail, with a fresh desktop screenshot when `include_screenshot` is true.
- `list_workflows`: the workflows that can be dispatched, with their parameters. A disabled workflow is listed too and cannot be dispatched until it is enabled.

## Start work

Confirm the agent, the workflow and the workspace with the person first: a job can spend the account's credit and is subject to its daily cap.

- `run_workflow`: start a named workflow now.
- `queue_workflow`: add a named workflow to the queue.
- `queue_jobs`: queue an agent workflow for one or more ticket keys.
- `dispatch_agent_job`: send a workflow to a named agent.

Every job runs in a workspace. If `workspace_slug` is missing, nothing is queued and the answer lists the active workspaces to pick from. `hint` is stored with the job, and a workflow step that declares a `hint` parameter receives it. `dispatch_agent_job` takes it inside `params`.

## Change the fleet

`manage_workspace` attaches an agent to a workspace or detaches it, and `set_agent_roles` sets the roles an agent may run. Both need the admin role.
