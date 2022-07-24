# example-k8s-infrastructure

Example of minikube cluster setup and organizing a CI/CD for deploying apps into it.

## System requirements

- Linux distribution (tested on Ubuntu 18.04)
- Python 3
- Ansible
- Python libs from requirements.txt

## Usage

### Editing inventory

In order to bootstrap infrastructure, you have to edit `hosts` file in root repo and add all variables needed by ansible
to special file in `host_vars` directory, which name matches machine domain in `hosts` file.
To check that ansible can reach your host, use the following command:

```bash
ansible all -u ansible -m ping
```

### Editing settings

Possible customisation:

- changing gitlab loal domain
- enabling|disbling running minikube dashboard
- and other

For doing this, consider editig custom roles in [roles filder](playbooks/roles)

Before editing, see doc for [gitlab](playbooks/roles/gitlab/README.md) and [run-minikube](playbooks/roles/run-minikube/README.md) custom roles.

### Running ansible-playbook

To install infra needed, run the following command:

```bash
  ansible-playbook playbooks/all.yml -e "ansible_become_password=YOUR_PASSWORD_HERE"
```

Hint: this way is not so secure, so we have to use ansible-vault to store secrets, but as PoC this is ok.
Note that command starts with spaces in order to prevent writing your password in history file.

Warning! This playbook edits your /etc/hosts files, if you stop using this app, don't forget to clean it up.

### Accessing Gitlab

After running ansible playbook, you can access your local Gitlab installation using URL and credentials
that are dynamically generated in file GITLAB_ACCESS.md in the root of this repo.

## Development

### Obtaining Galaxy roles

Before creating custom roles, we tries to fing suitable role on [Ansible Galaxy](https://galaxy.ansible.com).
This allows us to save time on role creation, testing and maintaining

In case you occasionly delete some of galaxy roles, you may get them back using following command:

```bash
ansible-galaxy install -r requirements.yml
```

### Creating custom roles

In order to fit best practice we create new roles by command:

```bash
cd playbooks/roles
ansible-galaxy init YOUR_ROLE_NAME
```

This is a little overkill (we don`t really want to publish roles to [Ansible Galaxy](https://galaxy.ansible.com)),
but this allows us to create same-looking roles and also use best practice for roles creating (like
directory structure, etc.)
