# bootstrap_playbook.md

## Runtime and dependency workflow examples

This file captures implementation playbooks that are intentionally excluded from operating bootstrap rules.

## Python workflow example

- Select target Python version before dependency setup.
- Set interpreter via Poetry.
- Add/update dependencies using current stable releases.
- Treat solver failures as explicit compatibility constraints.

## Node workflow example

- Select target Node version before dependency setup.
- Record runtime baseline (for example `.nvmrc`, `engines.node`).
- Create lockfile before upgrades.
- Upgrade dependencies non-interactively.
- Resolve failures through compatibility fixes, not ad hoc bypasses.

## Version policy notes

- Resolve versions from official registries at implementation time.
- Prefer stable releases unless project constraints require pinning.
- Document intentional downgrades or pins.
