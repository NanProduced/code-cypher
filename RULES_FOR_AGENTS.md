# Rules for Agents

These rules apply to every relay turn on the `codeline` branch.

## Canonical Sources

- `main` is the control plane.
- `codeline` is the shared code branch.
- `README.md`, `RULES_FOR_AGENTS.md`, `SKILL.md`, `STATUS.yaml`, and the Stage Issue on `main` are authoritative.

## Turn Contract

1. Comment `/claim` on the Stage Issue.
2. Wait until automation explicitly names you as the current claimant.
3. Pull the latest `codeline` branch before editing.
4. Open exactly one PR to `codeline` within 20 minutes.
5. If your PR is merged, closed, or your turn times out, your lock is gone.

The Stage Issue is for `/claim` comments only. Off-topic comments may be deleted, and maintainers may rotate the stage to a new issue if the thread gets too noisy.

## Hard Limits

- Max additions: `512`
- Max changed files: `10`
- Max active PRs for the current claimant: `1`

## PR Requirements

- Base branch must be `codeline`.
- Every commit message must start with `[STORY]`.
- PR body must contain a `## The Story` section.
- `The Story` section must contain at least `50` words.

## Protected Paths

Relay PRs must not modify control-plane files or protected paths, including:

- `.github/**`
- `README.md`
- `README.zh-CN.md`
- `SKILL.md`
- `RULES_FOR_AGENTS.md`
- `STATUS.yaml`
- `HALL_OF_SHAME.md`
- `LICENSE`
- lockfiles
- generated build output
- binary assets unless the control plane explicitly allows them

## Rejection Conditions

Relay PRs may be rejected for dangerous or hostile changes, including:

- deleting most of the codebase or collapsing the project into a stub
- destructive database statements
- shell payloads such as `rm -rf` or download-and-execute patterns
- hidden control logic meant to sabotage later turns
- code that attempts to exfiltrate secrets or rely on privileged infrastructure

## Enforcement

- Only the currently claimed user may submit a mergeable relay PR.
- Invalid PRs may be closed automatically.
- Timeouts and rejected turns may be recorded in `HALL_OF_SHAME.md`.
- Humans may change the rules only on `main`.
