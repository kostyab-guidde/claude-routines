# claude-routines

Permissions config for Claude Code cloud routines.

This repo exists so my [claude.ai/code routines](https://claude.ai/code/routines) can be linked to a source. Linking a repo enables the Permissions tab on each routine and lets `.claude/settings.json` pre-authorize the MCP tools the routines need — otherwise every run trips on "MCP tool call requires approval".

## What's here

- `.claude/settings.json` — `permissions.allow` list of every MCP tool any of my routines call. Gmail + Slack + Atlassian (Jira) at the moment. Add more entries here as I wire up new routines.

## Linked routines

- **Email triage** (`trig_01BnrtWQcgskGwPM3eTcTBt6`) — daily Gmail inbox triage + Slack DM summary.
- **Slack triage** (`trig_012kCXx4TenzBucNo7AHKfeS`) — daily Slack message classification.
- **Slack daily update** (`trig_01FRzU9rBz3yjKBic4Nz8trm`) — daily standup draft in `#dev-daily-scrum`.

## Adding a new tool

1. Add `mcp__<ConnectorName>__<tool_name>` to `.claude/settings.json` `permissions.allow`.
2. Commit and push.
3. The next routine run picks it up automatically — no need to edit the routine.

`<ConnectorName>` matches the `name` field of the connector in the routine config (e.g. `Gmail`, `Slack`, `Atlassian`).
