# claude-toolkit

My personal Claude Code toolkit, installable in any project.

- **software-team** (this repo): a team of eight specialist agents plus an orchestrator. Run `/software-team:team <what you want>`.
- **mattpocock-skills** (Matt Pocock's public plugin, installed separately): small skills such as `/grill-me`, `/to-spec`, `/tdd`, `/ask-matt`.

## Install on your computer or the desktop app (all projects)

Inside Claude Code, run these three commands, replacing `gopnikzxc`:

```
/plugin marketplace add gopnikzxc/claude-toolkit
/plugin install software-team@mwallq-toolkit
/plugin install mattpocock-skills@claude-plugins-official
```

Choose **user** scope if asked, so they apply to every project. Restart Claude Code, then type `/` and look for `software-team:team` and `grill-me`. In each project, run `/setup-matt-pocock-skills` once.

## Use in browser Claude Code (claude.ai/code)

Browser sessions start from your repository, so tell each repo about the plugins. Add the file `.claude/settings.json` to the repo with the contents of `project-settings-snippet.json` (replace the username), commit it, and start a new session. Claude Code will ask you to trust the marketplace the first time.

## Use the team

```
/software-team:team add per-user rate limiting to the public API
/software-team:team bug: CSV export drops rows that contain a newline
/software-team:team refactor the payment module
/software-team:team review
/software-team:team resume
/software-team:team-hire Postgres and migrations specialist
/software-team:team-retro
```

Notes:
- The team works on a `team/<slug>` branch with one commit per task and never pushes.
- Specialists you add with `team-hire` are stored in the project (`.claude/agents/` and `.team/roster-extra.md`), so they survive plugin updates.
- Changes to the core prompts are made in this repo. Edit a file on GitHub, commit, and update with `/plugin marketplace update mwallq-toolkit`.
- `settings.team.example.json` is optional: pre-approved read-only git and commits, blocked `git push`, hard resets and similar. Merge it into a project's `.claude/settings.json` or your own settings.

## Layout

```
.claude-plugin/marketplace.json        the marketplace definition
plugins/software-team/
  .claude-plugin/plugin.json
  agents/        eight team-* agents
  skills/        team (orchestrator), team-protocol, team-hire, team-retro
```
