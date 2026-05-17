---
name: spawn-subagent
description: Codex-only. Use when the user explicitly invokes `$spawn-subagent` in Codex and wants the following task to be executed by a suitable Codex subagent instead of the main agent. Routes the remaining user request to an appropriate subagent and keeps the main agent in coordinator mode.
disable-model-invocation: true
---

# Spawn Subagent

Use this skill as an explicit routing wrapper. The text after the skill invocation is the task to delegate. The main agent should not execute that task directly; it should choose a suitable subagent, call the Codex subagent tool, wait when needed, and return a concise synthesis.

This is not hard runtime routing. Codex still needs the main agent to call the subagent tool. Treat this skill as a standing instruction to make that call instead of doing the work locally.

## Routing Rule

When this skill is active:

1. Extract the delegated task from the user's message.
2. Choose the narrowest suitable subagent:
   - Use `explorer` for read-only research, codebase orientation, log/history inspection, documentation lookup, or evidence gathering.
   - Use `worker` for implementation, bug fixes, file edits, test updates, or other production work.
   - Use `default` when the task needs general reasoning and neither `explorer` nor `worker` fits.
   - Use a named custom agent when the user explicitly names one or the task clearly matches an available custom agent.
3. Spawn exactly one subagent unless the user explicitly asks for parallelism or the task naturally decomposes into independent branches.
4. Let Codex's subagent tool schema and system instructions govern the subagent input, permissions, and return shape.

## Do Not Execute Locally

Do not answer, research, implement, or debug the delegated task in the main thread except for the minimal work needed to route it safely. If subagent tools are unavailable, say that the task cannot be executed under `spawn-subagent` because delegation is unavailable; do not silently fall back to main-agent execution.

## Main-agent Output

Keep the final response short:

- Say which subagent was used.
- Give the subagent's direct answer or change summary.
- Include verification status or reasons verification was not run.
- Do not expand into a full second investigation in the main thread.
