# Home Lab Automation

> Ansible playbooks to fully configure my personal home lab.

## Usage

Given a propertly configured Proxmox host, the following will instantiate the entire home lab system from scratch:

```bash
ansible-playbook main.yml --ask-become-pass
```
