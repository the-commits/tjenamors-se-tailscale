# tjenamors-se-tailscale

[![sourcehut](https://img.shields.io/badge/sourcehut-~the--commits/tjenamors--se--tailscale-2d6b9e?logo=sourcehut)](https://git.sr.ht/~the-commits/tjenamors-se-tailscale)
[![GitHub mirror](https://img.shields.io/badge/GitHub-the--commits/tjenamors--se--tailscale-181717?logo=github)](https://github.com/the-commits/tjenamors-se-tailscale)

An Ansible role to install and configure [Tailscale](https://tailscale.com) VPN on Linux hosts.

- **Source:** [git.sr.ht/~the-commits/tjenamors-se-tailscale](https://git.sr.ht/~the-commits/tjenamors-se-tailscale)
- **Mirror:** [github.com/the-commits/tjenamors-se-tailscale](https://github.com/the-commits/tjenamors-se-tailscale) (read-only)
- **Issues / PRs:** sourcehut only (see CONTRIBUTING.md)

## Requirements

- Ansible 2.14+
- Root/sudo access on target hosts
- A Tailscale auth key (preferably reusable + ephemeral)

## Role Variables

| Variable | Required | Default | Description |
|----------|----------|---------|-------------|
| `tailscale_auth_key` | yes | `""` | Tailscale auth key (use Ansible vault) |
| `tailscale_extra_args` | no | `"--ssh"` | Extra arguments to pass to `tailscale up` |
| `tailscale_set_hostname` | no | `true` | Whether to set system hostname to `inventory_hostname` |
| `tailscale_hostname` | no | `""` | Explicit hostname (defaults to `inventory_hostname`) |

## Dependencies

None.

## Example Playbook

```yaml
- hosts: all
  become: true
  roles:
    - role: tailscale
```

## Vault

Store the auth key in your vault:

```bash
ansible-vault encrypt_string 'tskey-auth-...' --name 'tailscale_auth_key' >> group_vars/all/tailscale.yml
```

## License

AGPL-3.0
