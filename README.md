# doze-recall

**Context for coding agents: one picture of your whole system, from your code.**

doze-recall builds a graph of the apps in your repo and the links between
them (who sends to which queue, who reads which table, which route a client
calls) and serves it over MCP to Claude Code, Cursor, Codex or any other
agent. Every answer cites `file:line`, says how it was found, and says
whether it is complete.

It runs locally. It never calls an AI model to answer, and it never edits
your agent's files.

It is part of the [doze](https://github.com/doze-dev) family, and runs two
ways:

- **On its own**: one binary, pointed at your repo. Apps are found from their
  manifests, and resources are inferred from the names your code uses.
- **Inside doze**: add `recall {}` to `doze.hcl`. Links come from the stack
  you declared, and review happens in the dash.

**Status: in design.** Nothing here is built yet. The design lives in the
doze repo under `docs/design/recall/`.

## License

Apache 2.0.
