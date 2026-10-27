---
name: dont-stop-working
description: Carry an explicitly requested task through its remaining authorized work, verification, and an honest completion check. Use when the user asks to keep working until done or resume an unfinished completion loop.
---

# Don't Stop Working

Work toward the requested outcome until its acceptance criteria are verified or no useful authorized action remains. A checkpoint is not completion. Persistence does not expand the assignment or its permissions.

## Establish what done means

Recover the objective, accepted scope, constraints, and unfinished work from the conversation. If the user invokes this during an existing task, continue that task. Ask what to do only when no objective can be identified; do not invent work to keep busy.

Keep a compact completion ledger in working context. Use an existing task document when one belongs to the project; do not create files merely to demonstrate this process. For each acceptance criterion, record:

| Requirement | State | Evidence or blocker | Next action |
| --- | --- | --- | --- |
| The requested observable result | pending, working, verified, or blocked | What was actually checked, or what prevents it | The next authorized action |

Distinguish implementation, verification, commit/push, deployment, and publication when the task includes them. A generated artifact does not prove delivery, and a passing build does not prove the requested behavior.

## Match persistence to the actual runtime

The skill supplies instructions, not an execution service. Use only tools and continuation mechanisms exposed by the current host.

- **Codex with goal tools:** When the user's request authorizes a persistent goal and `get_goal`, `create_goal`, and `update_goal` are available, inspect the current goal first. Reuse a matching unfinished goal. Do not replace an unrelated goal. Create one only when the host permits it, and set a budget only when the user supplied one. Follow the tools' actual status and continuation rules; do not invent a retry count or claim a status transition that the tool rejected.
- **Codex without goal tools, or Claude Code:** Complete useful work within the active session and maintain the same ledger. Do not assume that task lists, compaction, hooks, or a task's presence automatically schedule another turn. If the host provides an authorized continuation mechanism, use it according to its contract.
- **At a real execution limit:** Preserve a concise resumption handoff in the conversation or an appropriate existing task record: objective, constraints, verified work, unresolved work, evidence, and exact next action. State that continuation is needed. Do not say a background worker is running unless one was actually started through an authorized mechanism.

Never install hooks, create daemons or shell retry loops, launch new CLI sessions, or obtain additional accounts to simulate persistence. This skill does not authorize any of those actions.

## Execute and verify

Repeat while useful authorized work remains:

1. Reconcile the latest user steering with the objective and ledger. A question or status request usually adds context; an explicit stop, pause, cancellation, or replacement changes what to pursue.
2. Choose the next actionable requirement. Resolve routine implementation choices with judgment and preserve unrelated work.
3. Do the work and verify the observable result at the level the requirement needs. Prefer focused checks; repeat or broaden them when a change, failure, or unresolved concern warrants it.
4. Update evidence, remaining work, and blockers. If another requirement is actionable, continue.
5. Run the completion check below before ending.

Do not end merely because one batch finished, tests passed, a commit was made, or a blocker appeared. If authorized work remains, perform it instead of offering to do it later or asking whether to continue.

Keep progress updates brief and follow the host's communication requirements. Explain material findings and the next action; do not repeatedly announce an unchanged blocker.

## Handle blockers without replaying actions

Record the exact failure and its effect on the outcome. Try a relevant authorized alternative when it can change the result, and continue independent requirements. Revisit blocked work when new information or external state makes progress possible.

Do not repeatedly retry an unchanged authentication challenge, quota, permission denial, or unavailable dependency. Before retrying an external write, inspect its outcome or use an existing idempotency mechanism so the action cannot be duplicated. An uncertain delivery remains uncertain until checked.

If user input is necessary, do independent work first when practical, then ask one specific question with the concrete prepared result. Ask sooner when the answer determines all remaining work or further work would be wasted. Silence does not grant approval.

Respect stops, budgets, execution limits, approval requirements, and the user's deployment, credential, spending, and external-action rules. A request to keep working does not authorize deployment, purchases, messages, or bypassing checks by itself.

## Completion check

Inspect every acceptance criterion before the final response:

- **Verified:** The requested result has observable evidence. No required, currently authorized implementation, verification, integration, delivery, or cleanup remains. Report the outcome and material limitations; mark a host-managed goal complete only when its requirements permit it.
- **Blocked:** No useful authorized action remains, and the outstanding requirements have specific blockers. Report what is incomplete, why, the work already prepared, and the minimum input or state change needed. Follow any host-managed blocked-status rules rather than manufacturing turns to reach a threshold.
- **Paused, cancelled, or limited:** Follow the user's stop or the host's limit. Preserve the task state without describing unfinished work as complete. Mark a host-managed goal paused only when the user requested a pause.

A truthful blocked or limited handoff is a valid stopping point. Partial progress described as verified completion is not.
