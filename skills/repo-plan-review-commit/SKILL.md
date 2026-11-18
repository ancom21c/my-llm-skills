---
name: repo-plan-review-commit
description: >-
  Plan, implement, review, and verify non-trivial repository changes such as features,
  fixes, refactors, or deployment and configuration edits. Use the repository's workflow
  and commit only when in scope. Applies to change requests that stop at a patch.
  Skip for read-only tasks and review-only requests.
---

# Repo Plan, Review, and Commit

## Establish scope and acceptance

- Read applicable repository instructions, check the working copy and staging state, and identify pre-existing changes. Preserve the user's work even when it overlaps the task.
- Write a short plan with the observable result and the check that will demonstrate it. Use the repo's planning workflow when required. Otherwise keep the plan in the session.
- If `docs/todo-workflow.md` applies, follow its artifact and completion conventions. Confirm which behavior, files, and side effects the task authorizes.

## Implement and verify

- Make the smallest coherent change that meets acceptance. Exercise the changed behavior through its normal entry point. Add or update regression coverage when required or when existing checks would miss a material failure mode.
- Use the repo's documented checks. Start with a focused check tied to acceptance, then run broader checks when required or when the change crosses a shared boundary. If no verification workflow is documented, pick checks that exercise the affected behavior. Scope automatic formatting to task-owned changes unless the repo requires a broader pass.
- Inspect the complete task patch, including new files and any staged changes. Check that the patch satisfies the request, preserves caller behavior, and covers relevant edge cases. Review authorization, sensitive data, migrations, failure recovery, or concurrency when the patch affects them.
- Fix findings in scope and rerun affected checks after the last relevant edit. Investigate failures before attributing them to the baseline. Report failed, skipped, and blocked checks with their reason and impact. Mark acceptance as unverified when evidence is missing. A narrower passing check cannot satisfy a required check with different coverage.

## Close task records when applicable

- Update plans, status labels, and active links to match actual acceptance evidence. Follow the repo's completion policy for archive, removal, and promotion of durable knowledge. Keep the task record if no policy governs its removal.
- If a task folder moves or is removed, update references to it in the same change. Keep completed work out of active entry points. Record reusable operational facts in the repo's documentation home when the change establishes them.

## Commit and hand off

- Commit only when the user requests a commit or applicable repo instructions explicitly require it for this task. Respect any user instruction to stop at the patch. Push only with explicit authorization.
- Before committing, inspect the exact commit contents. In Git, stage task-owned paths or hunks and inspect the index. If unrelated changes are already staged, use a commit method that leaves them staged and inspect the patch that method will commit. In Jujutsu, inspect all changes in the target revision, including files tracked automatically, and isolate task-owned changes before committing. If safe isolation is unclear, leave the working copy intact and report the blocker.
- After a commit, verify its contents and check that unrelated work remains intact. Report the delivered behavior, the checks run and their outcomes, remaining limits, and the commit ID if one was created.
