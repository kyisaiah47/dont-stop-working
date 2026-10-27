# Don't Stop Working

A skill for Codex and Claude Code that carries a task through the work you actually requested, including verification and an honest completion check.

It keeps a small ledger of requirements, evidence, blockers, and next actions. Finishing one patch or passing a test suite does not end the task while other authorized work remains.

## Example

> Fix the CSV import, verify duplicate handling, and update the import instructions. Keep working until all three are done.

The assistant tracks each result separately. If the integration environment is unavailable, it completes the local fix and documentation, records what it could verify, and reports the remaining integration blocker. It does not label the entire task complete or keep retrying the same outage.

## Install in Claude Code

From a Claude Code session:

```text
/plugin marketplace add kyisaiah47/dont-stop-working
/plugin install dont-stop-working@dont-stop-working-marketplace
```

Start a new session, then invoke:

```text
/dont-stop-working:dont-stop-working Finish the current task and verify each requested result.
```

To try a checkout for one session without installing it:

```bash
git clone https://github.com/kyisaiah47/dont-stop-working.git
claude --plugin-dir ./dont-stop-working
```

## Install in Codex

With a Codex version that supports plugin CLI installation:

```bash
codex plugin marketplace add kyisaiah47/dont-stop-working
codex plugin add dont-stop-working@dont-stop-working-marketplace
```

Start a new session, then invoke:

```text
$dont-stop-working Finish the current task and verify each requested result.
```

In a desktop client that exposes marketplace plugins through its directory, add the marketplace, select **Don't Stop Working**, and install it there. Available installation surfaces depend on the client version.

For standalone skill installation, copy only `skills/dont-stop-working/` into a skill directory supported by your host. Preserve any existing skill with the same name instead of overwriting it unintentionally. See the host's current skill-directory documentation.

## What persistence means

| Runtime | Behavior |
| --- | --- |
| Codex with exposed persistent-goal tools | Can reuse or create an authorized goal and follow the host's continuation and status rules. |
| Codex without those tools | Works within the active session and leaves a precise handoff at a real execution limit. |
| Claude Code | Uses the same completion ledger and verification method within the active session. An installed skill alone does not schedule future turns. |

The package installs no hooks, daemons, shell loops, MCP servers, or account-routing tools. It cannot guarantee unattended execution or bypass a runtime limit. Stop requests, budgets, permissions, and external-action approvals still apply.

## Validate a checkout

```bash
claude plugin validate --strict .
```

The [evaluation cases](evals/cases.md) cover behavior beyond metadata validation. The initial package was also checked with Codex's skill-creator validator and the portable Agent Plugins manifest schema. Those checks do not guarantee identical model behavior across hosts.

## Package

One shared `skills/dont-stop-working/SKILL.md` is used by both hosts. Root `plugin.json` provides the portable Agent Plugins manifest; `.claude-plugin/plugin.json` provides Claude packaging. Each host has its own repository marketplace catalog.

Copyright © 2026 Compound Labs. This is proprietary material distributed with permission for personal and business use; see [LICENSE](LICENSE).

Documentation: [Codex plugin packaging](https://developers.openai.com/plugins/build/plugins), [Claude Code plugins](https://code.claude.com/docs/en/plugins).
