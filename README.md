# Home Lab Automation

> Ansible playbooks to fully configure my personal home lab.

## Prerequisites

The host running these playbooks must have `ansible` installed.

```bash
apt install ansible
```

Additionally, the target host should have already been configured with a DNS-recognized hostname ("castle").

## Usage

The following will instantiate the entire home lab system from scratch:

```bash
./lab.yml
```
