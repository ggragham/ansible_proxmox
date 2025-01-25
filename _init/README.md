# Init Proxmox Configuration Ansible Playbook

## Description
An Ansible playbook for the initial setup of a Proxmox server.

## Dependencies
Before running the playbook, ensure that the required dependencies are installed on the host system where Ansible is executed:

- **sshpass**: For passing the SSH password.
- **python3-passlib**: Required for the `ansible.builtin.user` module (e.g., for hashing password during user creation).

On Fedora, you can install the dependencies with the following command:

```bash
sudo dnf install -y sshpass python3-passlib
```

## Usage
1. Copy the `inventory.ini.template` file to `inventory.ini` and fill in the details of your hosts.
2. Copy the `default.vars.yml` file to `vars.yml` and adjust it according to your requirements.
3. Run the playbook with the following command:
```bash
ansible-playbook init_playbook.yml -k
```
* `-k`: Prompts for the SSH password.
