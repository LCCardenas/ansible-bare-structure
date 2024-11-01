### Optional Ansible Configuration File

While not necessary for SSH configuration, Ansible does support a configuration file (`ansible.cfg`) where you can specify default behaviors, including SSH settings, to simplify your playbook executions:

You can place ansible.cfg in various locations, and Ansible will use the first one it finds:

1. In the directory where you're running Ansible.
2. In the user's home directory (`~/.ansible.cfg`).
3. In the system-wide directory (`/etc/ansible/ansible.cfg`).

### Playbook execution

From the project folder, do: `ansible-playbook -i inventory/hosts site.yml`