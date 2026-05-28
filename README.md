# Cisco NDFC Ansible Lab

This repository contains my Cisco NDFC automation Ansible playbook, python or many more


- Cisco NDFC
- Ansible
- `cisco.dcnm`
- REST API workflows
- Read-only prechecks before configuration changes

## Current Focus

The current playbooks focus on NDFC network attachment workflows:

1. Query network attachment state from NDFC.
2. Confirm the target network exists for the target leaf.
3. Read `isLanAttached` and `lanAttachState`.
4. Test NDFC REST attachment/deployment behavior in a lab.

## Repository Structure

```text
playbooks/
  NDFC_Module/
    Attach_network_without_ports.yml
inventory/
  inventory.example.yml
  group_vars/
    ndfc/
      vars.example.yml
  host_vars/
    DC1-Leaf1.example.yml
vars/
  network_attach_request.example.yml
```

## Safety

This repo contains only example inventory and variable files.

Do not commit:

- real NDFC passwords
- vault files
- private inventory
- real tokens
- local virtual environments

## Example Usage

Copy the example files before using the playbook in a lab:

```bash
cp inventory/inventory.example.yml inventory/inventory.yml
cp inventory/group_vars/ndfc/vars.example.yml inventory/group_vars/ndfc/vars.yml
cp inventory/host_vars/DC1-Leaf1.example.yml inventory/host_vars/DC1-Leaf1.yml
cp vars/network_attach_request.example.yml vars/network_attach_request.yml
```

Set credentials with environment variables:

```bash
export NDFC_USER='admin'
export NDFC_PASSWORD='your-password'
```

Run a playbook:

```bash
ansible-playbook -i inventory/inventory.yml playbooks/NDFC_Module/08_attach_network_without_ports.yml
```

## Notes

These playbooks are for lab learning and API behavior validation. Production workflows should add stronger validation, idempotency checks, change control handling, and post-change verification.
