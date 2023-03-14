# Ansible Role: Server Configuration

An Ansible role for configuring a Linux server. This role performs the following tasks:

- Set the server's timezone
- Disable password authentication and change the SSH port
- Add your authorized SSH key for authentication
- Disable IPv6
- Install atop, iftop, and fail2ban packages

## Requirements

This role requires Ansible 2.9 or higher and a Linux server to configure.

## Role Variables

This role does not have any required variables. However, you can customize the following variables in `defaults/main.yml`:

| Variable | Default Value | Description |
| -------- | ------------- | ----------- |
| `server_timezone` | `UTC` | The timezone to set on the server |
| `ssh_port` | `2222` | The new SSH port number to use |
| `ssh_authorized_key` | `~/.ssh/id_rsa.pub` | The path to your authorized SSH key file |
| `ssh_username` | `your_username` | The username to add the authorized SSH key to |
| `ipv6_enabled` | `true` | Whether to enable or disable IPv6 |
| `packages` | `[atop, iftop, fail2ban]` | The list of packages to install |

## Dependencies

This role has no dependencies on other Ansible roles.

## Example Playbook

Here's an example playbook that uses this role:

```yaml
- name: Configure server
  hosts: your_server_hostname
  become: true
  roles:
    - server-configuration
