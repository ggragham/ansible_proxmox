# Proxmox Configuration Ansible Playbook

A bunch of Ansible playbooks to automate the configuration of a Proxmox environment, including Proxmox VE and Proxmox Backup Server.

# Table of Contents
- [Prerequisites](#prerequisites)
- [Usage](#usage)
- [Note](#note)
- [Author](#author)
- [License](#license)

# Prerequisites
- Ansible installed
- Access to a Proxmox VE and/or Proxmox Backup Server

# Usage
0. Clone the repository and change into its directory:
```bash
git clone https://github.com/ggragham/ansible_proxmox.git && cd ansible_proxmox/
```
1. Copy the inventory file template (`inventory.ini.template`) to `inventory.ini` and adjust it for your server.
2. Use the default playbooks and variables files as templates for your configuration:
   - `default.pve.playbook.yml` / `default.pve.vars.yml` for Proxmox VE
   - `default.pbs.playbook.yml` / `default.pbs.vars.yml` for Proxmox Backup Server

   Rename them as needed (e.g., `pve.playbook.yml`/`pve.vars.yml` or `pbs.playbook.yml`/`pbs.vars.yml`). These files will be excluded from Git (see [`.gitignore`](./.gitignore)).
3. Make sure your playbook points to the correct variables file in `vars_files`, for example:
```yaml
- hosts: pve
  become: true

  vars_files: [pve.vars.yml]
  # ...
```
4. Configure host-specific variables in the `host_vars` directory. Use `host_vars/pve1.yml.template` as a template and rename it to match your inventory hostname, for example `host_vars/pve1.yml`.
5. Place your SSL certificate, SSH key, VPN configuration, etc., in the `./assets` directory, and reference them in your variables file.
6. Install the Ansible roles listed in the `requirements.yml` file:
```bash
ansible-galaxy role install --force --role-file requirements.yml
```
7. Run your chosen playbook using:
```bash
ansible-playbook pve.playbook.yml
```
You can also use the `--tags=""` and/or `--skip-tags=""` options to include or exclude tasks. For example:
```bash
ansible-playbook pve.playbook.yml --tags="base,network" --skip-tags="external_disks"
```

# Note
Some tasks intentionally use `command` and `shell` because the community Proxmox modules are too buggy and unreliable for this setup.

This was made for personal use and learning. Feel free to use it as a template for your own setup.

# Author
This project was created by [Grell Gragham](https://github.com/ggragham).

# License
This software is published under the DO WHAT THE FUCK YOU WANT TO PUBLIC LICENSE license.
