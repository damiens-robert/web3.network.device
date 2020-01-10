# Ansible Role: hosts

## Description

Ansible role that dynamically creates the hosts file.

## Requirements

[molecule v2.22](https://molecule.readthedocs.io/en/stable/)

## Installation

git clone https://github.com/damiens-robert/web3.network.device.git

## Usage

### Prerequesites

In the project folder.

```
echo "your_password_for_protecting_the_ansible_vault" > password.txt
```

In the vars folder.

Edit password.vault file with your system sudo password.

In the vars folder.

```
ansible-vault encrypt password.vault --vault-password-file ../password.txt
```

In the vars folder.

```
cp hosts.yml.example hosts.yml
```

Edit hosts.yml file.

### Run

In the project folder.

```
HOSTNAME=$(hostname) molecule converge
```

## Role Variables

### hosts_backup

Set the host file path.

```yml
hosts_file: '/etc/hosts'
```

Backup the hosts file before changing it.

```yml
hosts_backup: true
```

### hosts_owner

Owner of hosts file.

```yml
hosts_owner: root
```

### hosts_group

Group owner of hosts file.

```yml
hosts_group: root
```

### hosts_mode

Access permission hosts file.

```yml
hosts_mode: 0644
```

### SELinux

Settings for SElinux.

```yml
hosts_serole: object_r
hosts_setype: net_conf_t
hosts_seuser: system_u
hosts_selevel: s0
```

### Loppback

Creates a 172.0.0.1 entry for the server name.

```yml
hosts_hostname_loopback: true
```

### Inventory

Inserts all hosts in the Ansible Inventory file into the Hosts file.

```yml
hosts_inventory_to_hosts: false
```

For `hosts_inventory_to_hosts` to work, the variable `internel_ansible_host` must be set in the `host_vars`, alternative can also be set to `ansible_host`.
Optionally, `hosts_aliases` can be set in the `host_vars`, then it generates aliases for the hosts.

### IPv6

Ipv6 localhost entries are set automatically. Setting false it can be prevented.

```yml
hosts_ipv6: true
```

## Dependencies

None

## Author

- [Damiens ROBERT](https://www.linkedin.com/in/damiens-robert-72b3a417/)

## License

This project is under the MIT License. See the [LICENSE](LICENSE) file for the full license text.
