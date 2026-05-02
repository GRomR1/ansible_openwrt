# `flyoverhead.openwrt.chronyd`

Configure `chrony` NTP client and server on OpenWrt.
- Installs `chrony`
- Disables `sysntpd`
- Configures `chrony` as NTP client for external pools
- Configures `chrony` as NTP server for LAN clients
- Adds firewall rule to allow NTP access from LAN

## Role Variables

| Variable | Description | Status | Type | Default |
| :--- | :--- | :--- | :--- | :--- |
| `chronyd_pools` | List of NTP pools | `optional` | `list` | `["pool.ntp.org"]` |
| `chronyd_allow_subnets` | List of subnets allowed to access NTP server | `optional` | `list` | `[]` (auto-discovered from LAN if empty) |
| `chronyd_pkgs` | Packages to install | `optional` | `list` | `["chrony"]` |
| `chronyd_makestep_threshold` | Makestep threshold | `optional` | `float` | `1.0` |
| `chronyd_makestep_limit` | Makestep limit | `optional` | `integer` | `3` |
| `chronyd_driftfile` | Path to drift file | `optional` | `string` | `/var/lib/chrony/drift` |
| `chronyd_logdir` | Path to log directory | `optional` | `string` | `/tmp/log/chrony` |

## Dependencies

| Name | Description |
| :--- | :--- |
| `Ansible Role: openwrt` | [Ansible role by gekmihesg](https://github.com/gekmihesg/ansible-openwrt) for managing OpenWRT |

## Example Playbook

```yaml
- hosts: openwrt
  roles:
      - role: flyoverhead.openwrt.chronyd
```

## License

GPL-3.0
