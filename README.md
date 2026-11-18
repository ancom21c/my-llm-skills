# My LLM Skills

A collection of Agent Skills for coding workflows. Each skill lives in its own directory under `skills/` and starts with a `SKILL.md` file.

## Skills

| Skill | When to use it |
| --- | --- |
| [repo-plan-review-commit](skills/repo-plan-review-commit/SKILL.md) | Plan, implement, review, and verify a non-trivial repository change. Preserve existing work and commit only when the task calls for it. |

## Install in Codex

Ask Codex to install the skill from this repository.

```text
$skill-installer Install the skill at skills/repo-plan-review-commit from https://github.com/ancom21c/my-llm-skills.
```

You can also clone the repository and copy the entire skill directory, including `agents/`, into `${CODEX_HOME:-$HOME/.codex}/skills/`.

## Use

Invoke the skill in the repository you want to change.

```text
Use $repo-plan-review-commit to fix the failing CSV import and leave the result as a patch.
```

This request asks Codex to implement and verify the fix and leave it ready for review. Ask for a commit in the prompt if you want one.
