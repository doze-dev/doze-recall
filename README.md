# doze-recall

**Context for coding agents that doesn't have to be learned twice.**

Every agent session starts cold: it lists folders, greps, and re-reads the
same files to work out what each app does, how the apps connect and where
code lives. The next session does it all again. doze-recall keeps what has
been learned and hands it to the next session cheaply.

It gives an agent two things:

- **Facts,** generated from your code and never written by AI: a compact
  tree of each app (folders, entrypoints, tests, migrations, the functions
  and types in each file), checked against the files on every call, so it's
  never out of date. In a [doze](https://github.com/doze-dev/doze) stack, it
  also has a map of the whole stack: the apps, what each is wired to, and the
  databases, queues, topics and buckets between them.
- **Knowledge,** written by agents as they work: what an app does, its
  routes and consumers, flows across apps, conventions and gotchas. It's
  plain markdown in `.recall/`, committed with your code. Each piece cites
  the files it came from and says when they've changed. Anything a person
  edits is never overwritten.

## Two ways to use it

**In a doze stack,** add one line to `doze.hcl`:

```hcl
recall {}
```

doze runs recall as part of the stack, an MCP server that sleeps when no
agent is connected. Connect your agent:

```sh
claude mcp add recall -- doze recall mcp
```

**On its own,** for one project with no doze, it's a command-line tool:

```sh
doze-recall tree                 # the project's tree
doze-recall notes                # what's been learned, marked fresh or stale
doze-recall remember app:billing --sources <files> < note.md
```

Output is markdown sized to fit a prompt, for you to paste or for your
agent to run.

Go, TypeScript, JavaScript, Python and Rust.

**Status: in design.** Nothing here is built yet.

## License

Apache 2.0.
