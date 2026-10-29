# skills

Prompt skills for Claude (and any agent that reads [Agent Skills](https://agentskills.io)).

## deepen

**Deeper, not bigger.** This replays the prompt:

> i want a deeper version of the above task, not a bigger one. Before rewriting it: a. say what a top professional in this field would do here that I'm not asking for; b. name the rawest material from where they would start instead of what has already been digested for me; c. name the specific methods and tools they would use; d. say what, other than you or me, would show the result is right. Then rewrite my prompt to ask for exactly that.

It answers a–d, then gives a rewritten prompt you can copy as-is. With `--go`, it runs that rewrite immediately. It fetches the raw material where it can, says plainly what it can't get, and runs the outside check and reports pass or fail.

| You type | What happens |
|---|---|
| `/deepen` | Deepens the most recent task in the conversation |
| `/deepen <task>` | Deepens the task you typed |
| `/deepen --go` (or `/deepen go`) | Deepens it, then runs the rewritten prompt |

Pasting the original prompt by itself also triggers the skill.

See [`examples/mfa-artist-statement.md`](examples/mfa-artist-statement.md) for a real run.

## Install

**Claude Code, as a plugin** (invoke as `/sebskills:deepen`):

```
/plugin marketplace add cbassuarez/skills
/plugin install sebskills@sebskills
```

**Any agent, with the skills CLI:**

```
npx skills add cbassuarez/skills@deepen
```

**By hand** (invoke as `/deepen`): copy `skills/deepen/` into `~/.claude/skills/`. Or, to keep editing it in this repo, symlink it instead:

```
ln -s "$PWD/skills/deepen" ~/.claude/skills/deepen
```

**Claude.ai:** zip the `skills/deepen/` folder and upload it in Claude's Skills settings.

## Layout

```
skills/deepen/SKILL.md        the skill (portable Agent Skills frontmatter)
.claude-plugin/plugin.json    makes this repo a Claude Code plugin ("sebskills")
.claude-plugin/marketplace.json  makes it installable via /plugin marketplace add
examples/                     sample outputs
```

To add another skill, create `skills/<name>/SKILL.md`. It gets picked up by all of the install routes above.

## License

MIT. See [LICENSE](LICENSE).
