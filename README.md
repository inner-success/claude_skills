# Claude Code Skills

A collection of custom skills for [Claude Code](https://docs.anthropic.com/en/docs/claude-code).

## human_training

Reviews the prompts and instructions you gave during a session and teaches you how to improve your AI instruction skills across 5 disciplines:

1. **Prompt Engineering** -- clarity, examples, guard rails, output format, XML structure
2. **Context Engineering** -- pre-loaded resources, token efficiency, document structure
3. **Intent Engineering** -- session goals, values, decision boundaries, priority order
4. **Specification Engineering** -- governance, progress logs, quality assessment, verification
5. **Agent and Workflow Engineering** -- workflow patterns, tool definitions, safety, state management

It also provides a token usage analysis comparing your actual session cost against an optimised estimate.

### Installation

Copy the `human_training` folder into your Claude Code skills directory:

```
~/.claude/skills/human_training/SKILL.md
```

Or clone this repo and copy it:

```bash
git clone https://github.com/inner-success/claude_skills.git
cp -r claude_skills/human_training ~/.claude/skills/
```

### Usage

In any Claude Code session, type:

```
/human_training
```

Claude will review all your prompts from the current session and provide detailed feedback with actionable improvements tagged as `[ERROR RISK]` or `[GOOD PRACTICE]`.

## License

MIT
