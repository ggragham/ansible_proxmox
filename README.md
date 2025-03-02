# Proxmox Configuration Ansible Playbook

A bunch of Ansible playbooks to automate the configuration of a Proxmox environment.

# Table of Contents
- [Prerequisites](#prerequisites)
- [Usage](#usage)
- [Note](#note)
- [Author](#author)
- [License](#license)

# Prerequisites
- Ansible installed
- Access to a Proxmox server

# Usage
0. Clone the repository and change into its directory:
```bash
git clone https://github.com/ggragham/ansible_proxmox.git && cd ansible_proxmox/
```
1. Copy the inventory file template (`inventory.ini.template`) to `inventory.ini` and adjust it for your server.
2. Use `default.vars.yml` and `default.playbook.yml` as templates for your configuration. Rename them as needed (e.g., `proxmox_server.vars.yml`/`proxmox_server.playbook.yml`). These files will be excluded from Git (see [`.gitignore`](./.gitignore)).
3. Place your SSL certificate, SSH key, VPN configuration, etc., in the `./assets` directory, and reference them in your variables file.
4. Run your chosen playbook using:
```bash
ansible-playbook proxmox_server.playbook.yml
```
You can also use the `--tags=""` and/or `--skip-tags=""` options to include or exclude tasks. For example:
```bash
ansible-playbook proxmox_server.playbook.yml --tags="base,network" --skip-tags="external_disks"
```

# Note
This was made for personal use and learning. Feel free to use it as a template for your own setup.

# Author
This project was created by [Grell Gragham](https://github.com/ggragham).

# License
This software is published under the DO WHAT THE FUCK YOU WANT TO PUBLIC LICENSE license.
