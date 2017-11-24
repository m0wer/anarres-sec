# Sec

Ansible role for basic GNU/Linux server hardening.

It is part of [anarres](https://git.hdg.sh/anarres/anarres), a playbook that
uses a collection of roles to deploy a full-featured server. But it can be used
and tested independently.

## Compatibility

These are the tested GNU/Linux distributions. Maybe it works on some other
distributions too or just requieres a few changes.

* [debian](https://www.debian.org/)
	* stretch

## Requirements

`sudo` and `python`.

## Role Variables

### SSHd

* `ssh_port`: Port for `sshd` to bind to.

### sendxmpp

* `admin_xmpp`: Jabber account of an administrator. Will receive `fail2ban`
notifications.
* `sendxmpp_config`: `snedxmpp` configuration file path.

### fail2ban

* `fail2ban_trusted`: `fail2ban` trusted IPs, hosts or ranges.
* `fail2ban_xmpp_notify`: address used by `fail2ban` to send notifications to.
By default is the same as `admin_xmpp`.

### iptables

* `iptables_rules_general`: Default `iptables` rules.
* `iptables_rules_logging`: Default `iptables` logging rules. They will be
placed at the end.

## Dependencies

* [anarres/anarres-common](https://git.hdg.sh/anarres/anarres-common)

## Example playbook

```yaml
- hosts: all
  roles:
  	- anarres-common
    - anarres-sec
```

## Testing

To test the role you need [molecule](http://molecule.readthedocs.io/en/latest/)
.

```bash
molecule test
```

There is more documentation about the installation and configuration of the
required tools at
[wiki-testing](https://git.hdg.sh/anarres/anarres/wiki/testing).

## License

GPLv3

## Author Information

m0wer: m0wer (at) autistici.org
