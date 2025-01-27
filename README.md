### Optional Ansible Configuration File

While not necessary for SSH configuration, Ansible does support a configuration file (`ansible.cfg`) where you can specify default behaviors, including SSH settings, to simplify your playbook executions:

You can place ansible.cfg in various locations, and Ansible will use the first one it finds:

1. In the directory where you're running Ansible.
2. In the user's home directory (`~/.ansible.cfg`).
3. In the system-wide directory (`/etc/ansible/ansible.cfg`).

### Playbook execution

As a best practice, it's advisable to create the `ansible` user initially to bootstrap the system. For security reasons, among others, it's preferable to avoid running the playbook as the root user.

In order to create a dedicated Ansible user, run `ansible-playbook -i inventory/hosts bootstrapping.yml`. It requires an ssh key, which you need to add in `roles/common/files/ansible.pub`. Run the role using either the `root` user or a user that can do `sudo`. Once the Ansible user has been created, modify the `ansible.cfg` file and set the parameter `remote_user` to `ansible` and use the private key file you created for that user. 

Nevertheless, if creating an Ansible user is deemed unnecessary, you can run the playbook with the current user. However, if this user is not `root`, ensure it has `sudo` capabilities, since it needs enough permissions to update and upgrade the system. You can then execute the common role using the following command: `ansible-playbook -i inventory/hosts site.yml.`