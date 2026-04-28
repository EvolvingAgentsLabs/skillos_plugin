# skillos

Claude Code plugin that adds the `/skillos` command. Give it a goal — it creates specialized agents, executes them, logs traces, and consolidates learnings.

Part of the [Evolving Agents](https://github.com/EvolvingAgentsLabs) ecosystem.

## Install

From the marketplace:

```bash
/plugin marketplace add evolving-agents-labs/skillos_plugin
/plugin install skillos-plugin
```

From a local directory:

```bash
/plugin install /path/to/skillos_plugin/skillos-plugin
```

## Use

```bash
/skillos "Plan a weekly menu for 4 people"
/skillos "Build a REST API with auth and tests"
/skillos dream
/skillos dream authentication
```

## How it works

When you provide a goal, `/skillos` decomposes it into tasks and creates specialized agents as markdown files — typically a triad of implementation, quality, and integration agents. Each agent is executed via the Task tool, and every interaction is logged as a memory trace. After execution, a consolidation step extracts patterns and learnings into long-term memory so future projects can reuse proven strategies. The `dream` subcommand triggers consolidation on demand, optionally scoped to a specific goal.

## License

Apache 2.0
