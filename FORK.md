# Why this fork exists

`centralize-inc/ponytail` is a fork of [DietrichGebert/ponytail](https://github.com/DietrichGebert/ponytail).
It exists for two reasons.

**To freeze the version.** Devin's plugin manifest has no field that pins a tag or a commit. A new
Devin session re-fetches the plugin from its default branch. If the manifest pointed at the upstream
repo, every merge upstream would reach every Devin session in this org with no review. Pointing at
this fork makes our own merge the release.

**To remove rules that contradict our repo rules.** `AGENTS.md` loads in full in every Devin
session, in every repo. Upstream states specific conventions for comments, tests, and file count
that disagree with `CLAUDE.md` in `centralize-inc/Web`. This fork replaces each one with a
deferral to the conventions of the repo the agent is in. Skill files are unchanged.

## To review what upstream changed

```bash
git remote add upstream https://github.com/DietrichGebert/ponytail.git
git fetch upstream
git diff HEAD upstream/main -- AGENTS.md skills/
```

Take what you want. Keep the deferrals above. The other 151 files in this repo target agents we do
not use, and Devin does not read them.

## Install

The manifest entry lives at Settings → Resources → Plugins in Devin:

```json
{ "optionalPlugins": ["centralize-inc/ponytail"] }
```
