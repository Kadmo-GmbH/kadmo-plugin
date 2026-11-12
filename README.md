# Kadmo

Kadmo runs AI agents on your team's tickets. This plugin connects Claude Code or Cursor to your Kadmo account through Kadmo's hosted MCP server, so you can dispatch work to your agents, follow tasks and runs, and edit your knowledge pack and playbooks from your coding tool.

## What's in it

- **The MCP server**, `https://app.kadmo.ai/mcp` (Streamable HTTP, OAuth). You see the tools your role in the account allows.
- **Three skills** that use it:
  - `kadmo-work-on-ticket`: run a playbook on a ticket and follow the run.
  - `kadmo-fleet`: check your agents and dispatch a workflow to one.
  - `kadmo-skill-pack-authoring`: change a knowledge-pack file safely.

## Install

Claude Code:

```bash
claude plugin marketplace add Kadmo-GmbH/kadmo-plugin
claude plugin install kadmo@kadmo
```

Then run `/mcp`, pick `kadmo` and choose **Authenticate**.

Cursor: install **Kadmo** from the marketplace or add this repository as a plugin, then sign in when Cursor shows the `kadmo` server under MCP.

Claude.ai: add a custom connector with the URL `https://app.kadmo.ai/mcp`.

## Sign-in

The server signs you in over OAuth with your Kadmo account. Your client registers itself, so there is no client id to copy. For a headless client, create a personal token on the Connect card in Kadmo and send it as a bearer token.

## What the tools can do

Tools are marked read-only or destructive. Dispatching a job runs it on one of your account's agents. A job can spend your account's credit and is subject to its daily cap. Text you add to a job is stored with it, shown in Kadmo and available to the agent as context.

## Links

- Documentation: <https://docs.kadmo.ai/mcp/overview>
- Tool reference: <https://docs.kadmo.ai/mcp/tools>
- Privacy: <https://kadmo.ai/privacy>
- Terms: <https://kadmo.ai/terms>
- Support: <https://kadmo.ai/support>

## Licence

Apache-2.0, see [LICENSE](LICENSE). The licence covers this repository: the manifests, the skills and the documentation. The Kadmo service and the `@kadmo/cli` package have their own terms.
