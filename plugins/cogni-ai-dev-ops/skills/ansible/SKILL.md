---
name: ansible
description: >-
  Execute and manage Ansible playbooks and commands safely, preventing hangs
  during remote automation. You MUST load this skill when working with the
  `ansible` command.
license: MIT
---
<!-- markdownlint-disable MD013 MD023 MD031 MD032 -->

# Ansible Operations

## WHEN TO USE

- Executing Ansible playbooks or commands
- Running Ansible automation scripts
- Troubleshooting hangs during Ansible execution

## WHEN NOT TO USE

- Localized script automation on a single machine (use shell scripts)
- Ephemeral container infrastructure (use Docker or Terraform)
- Tasks requiring agentic AI decisions (Ansible is deterministic)
- General shell scripting (use `shell` skill)
- Docker operations (use `docker` skill)

## Common Pitfalls

- **Interactive Hangs**: Missing `DEBIAN_FRONTEND=noninteractive` or handling sudo passwords poorly, causing indefinite hangs.
- **Ignoring Idempotency**: Using `ansible.builtin.shell` instead of native modules, breaking playbook idempotency.
- **Masking Errors**: Using `ignore_errors: yes` to bypass failures rather than fixing the underlying state.
- **Mocking Workarounds**: Using `mock_modules` or `mock_roles` to bypass failing tasks. Fix underlying issues directly.

## Troubleshooting

### Ansible Environment Issues

For hangs during Ansible execution (especially `apt` on Debian/Ubuntu):

- Set `DEBIAN_FRONTEND=noninteractive` in environment or playbook:
  `DEBIAN_FRONTEND=noninteractive ansible-playbook playbook.yml`

## Performance Profiling

Enable `profile_tasks` callback to identify slow tasks:

- `ANSIBLE_CALLBACKS_ENABLED=profile_tasks ansible-playbook playbook.yml`
- In `ansible.cfg`:
  ```ini
  [defaults]
  callbacks_enabled = ansible.posix.profile_tasks
  ```

## Examples

- Run a playbook: `ansible-playbook -i inventory.yml site.yml`
- Run with tags: `ansible-playbook playbook.yml --tags "setup,deploy"`
- Check mode: `ansible-playbook playbook.yml --check --diff`
- Ping all hosts: `ansible all -i inventory.yml -m ping`

## Related Skills

- **molecule**:
  You MUST load this skill when running or managing Molecule tests for Ansible.
