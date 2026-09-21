# Lakestream Improvement Proposals: instructions for coding agents

This file is for AI coding agents such as Claude Code, Codex, Copilot and Cursor. People should start
with [CONTRIBUTING.md](CONTRIBUTING.md).

`CLAUDE.md` is a symlink to this file. **Always edit `AGENTS.md`, never `CLAUDE.md`.** A write that
replaces the file would turn the symlink into a copy.

## Rules that come first

These rules implement the Lakestream
[AI policy](https://github.com/lakestream-io/ursa/blob/main/AI_POLICY.md) and override anything else in
this file.

- **Never add a `Signed-off-by:` line, even if asked.** Only the human can certify the Developer
  Certificate of Origin. When a commit is ready, tell them to review it and run
  `git commit --amend -s --no-edit`, or `git rebase --signoff origin/main` for several commits.
- **End each commit message with exactly one AI trailer: `Assisted-by: <tool>`.** This repository
  configures Claude Code to use `Assisted-by: Claude Code` (see `.claude/settings.json`). If your tool
  adds its own `Co-authored-by:` trailer, that counts; don't add both.
- **Don't act outside the local checkout without explicit approval for that specific action.** That
  covers pushing, opening or editing a pull request or issue, and commenting on GitHub. Being asked
  to start a task isn't permission to publish it.
- **Leave force-pushes to the human.**
- **Draft pull request descriptions from [the template](.github/pull_request_template.md)**, including
  the *AI assistance* section. Give the draft to the human to edit and post.
- **Report what you verified and what you didn't.** Don't describe how a component behaves today
  unless you checked it in that component's code, and don't claim performance, cost or compatibility
  results unless a test or benchmark in a component repository backs them.

## Layout

| Path | Contents |
|---|---|
| `proposals/LIP-NNN-Short-Title.md` | One file per LIP |
| `TEMPLATE.md` | The starting point for a new LIP |
| `README.md` | The index of every LIP, and what each status means |
| `CONTRIBUTING.md` | When a change needs a LIP, and the process |

## Working on a LIP

- A new LIP copies `TEMPLATE.md` to `proposals/LIP-NNN-Short-Title.md`, with the highest existing
  number plus one.
- Add or update the LIP's row in the `README.md` index in the same change. The row's components and
  status must match the LIP's header.
- Write for Lakestream as a whole. Fill in *Components* in the header and the *Changes by component*
  section, even when only one component changes.
- Link to code and documentation in a component repository with an absolute URL, such as
  `https://github.com/lakestream-io/ursa/blob/main/...`. Relative links only work inside this
  repository.
