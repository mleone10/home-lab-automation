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

### Creating VMs

To simplify automation, new VMs are created manually. Template VMs are provided to simplify this process, but some manual configuration is still necessary. After this procedure, the new VM should be accessible via a custom hostname.

1. From the Proxmox GUI, clone one of the template VMs.
1. Modify the new VM to suit its needs (memory, disk space, network devices, etc.)
1. Start the VM and log in using `ssh mleone@debian`, referencing the default hostname
1. Run `sudo updateVmHostname <hostname>`. This will update the VM's hostname and renew the DHCP lease.
