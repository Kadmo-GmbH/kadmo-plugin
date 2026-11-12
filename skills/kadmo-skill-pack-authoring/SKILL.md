---
name: kadmo-skill-pack-authoring
description: Change a file in a Kadmo knowledge pack without overwriting someone else's edit. Use when someone asks to add or update what Kadmo's agents know about an app, a module or a role.
---

# Author a Kadmo knowledge pack

This skill uses the `kadmo` MCP server's tools. Writes need the admin role.

1. **Orient.** `get_pack` returns the pack's repo, its domains, and what a write does there: a commit, a push, a pull request, or a refusal. On a pull-request pack nothing is live until a person merges.
2. **Find the file.** `list_pack_files` lists the pack's files with their `base_sha`.
3. **Read it.** `read_pack_file` returns the content and the `base_sha` to send back. If it reports `truncated: true`, read again with `max_bytes` of at least `bytes`, because a shortened body written back deletes the rest of the file.
4. **Check the edit.** Call `write_pack_file` with the file's complete new body, its `base_sha` and `dry_run: true`. It runs every check and writes nothing.
5. **Write.** Call it again without `dry_run`. If it answers `stale_base_sha`, someone else changed the file: apply your edit to the content that answer carries and send it with the new sha.
6. **New areas.** `scaffold_pack_node` creates a new domain or module with its starter files.
7. **Say when it lands.** A commit is live in the portal at once and reaches agents within about five minutes.

Workflow YAML is read with `read_pack_file` and `workflow`, not `path`: a shared default workflow reads back empty by path. It is written through `manage_workflow` with `action: "edit_source"` and the `base_sha` of that read, which also makes the account's copy the one that runs. Names in a pack follow the library's rules: pack titles and module names read as plain noun phrases and do not repeat a word between a child and its pack.
