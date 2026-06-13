# tjenamors-se-tailscale

An Ansible role to install and configure [Tailscale](https://tailscale.com) VPN on Linux hosts.

## Requirements

- Ansible 2.14+
- Root/sudo access on target hosts
- A Tailscale auth key (preferably reusable + ephemeral)

## Role Variables

| Variable | Required | Default | Description |
|----------|----------|---------|-------------|
| `tailscale_auth_key` | yes | `""` | Tailscale auth key (use Ansible vault) |
| `tailscale_extra_args` | no | `""` | Extra arguments to pass to `tailscale up` |

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
