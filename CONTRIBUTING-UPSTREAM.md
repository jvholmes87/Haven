# Contributing our changes back to Haven

This fork exists to run one community. The safety features we add are useful to any Haven server, so each one goes back to [ancsemi/haven](https://github.com/ancsemi/haven) as its own pull request.

## Rules for an upstream branch (`upstream/<feature>`)

1. One feature per branch, started from the latest `main` (which tracks upstream).
2. Generic: the feature is an **opt-in server setting**, off by default, with the same look as Haven's existing settings. Nothing changes for servers that do not turn it on.
3. Sanitised: no project names, studio names, domains, tracker IDs, internal links or people. Commit messages and PR text describe the feature, not our reasons for needing it beyond "servers with minors or public signups".
4. Tested: a `test/<feature>.test.js` that runs under `node --test`, and the full suite green.
5. Documented: a short section in `GUIDE.md` in Haven's own voice, and a line under "Unreleased" in `CHANGELOG.md` in Haven's format.
6. Follows upstream's `SECURITY.md` for anything security-related: private report first if the change fixes a weakness.
7. Opened as a draft PR with the issue it answers linked; one maintainer review round at a time; no force-pushes after review starts.

## Before the first PR

Open one upstream issue that lists the planned features (the table in `forkline/README.md`, without the studio column) and asks whether the maintainer wants them as opt-in settings. The issue text is kept in `forkline/upstream-issue.md` and is posted by the project owner, not by an automated tool.

## What never goes upstream

- Our theme, wording, rules page, parent page, deployment files.
- Anything in `forkline/`.
