# Home Lab Automation

> Ansible playbooks to fully configure my personal home lab.

## Prerequisites

The host running these playbooks must have `ansible` installed.

```bash
apt install ansible
```

Additionally, the target Proxmox host should have already been configured with a DNS-recognized hostname ("castle01").

## Usage

The following will instantiate the entire home lab system from scratch:

```bash
./lab.yml
```

This works because the `lab.yml` playbook has been made executable and has a shebang pointing to `ansible-playbook`. Individual playbooks found in the `playbooks` directory can similarly be executed.
