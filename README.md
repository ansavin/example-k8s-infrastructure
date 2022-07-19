# example-k8s-infrastructure

Example of minikube cluster setup and organizing a CI/CD for deploying apps into it.

## Usage

### Editing inventory

In order to bootstrap infrastructure, you have to edit `hosts` file in root repo and add all variables needed by ansible
to special file in `host_vars` directory, which name matches machine domain in `hosts` file.
To check that ansible can reach your host, use the following command:

```bash
ansible all -u ansible -m ping
```

### Running ansible-playbook

To install infra needed, run the following command:

```bash
  ansible-playbook playbooks/all.yml -e "ansible_become_password=YOUR_PASSWORD_HERE"
```

Hint: this way is not so secure, so we have to use ansible-vault to store secrets, but as PoC this is ok.
Note that command starts with spaces in order to prevent writing your password in history file.

## Development

### Obtaining Galaxy roles

In case you occasionly delete some of galaxy roles, you may get them back using following command:

```bash
ansible-galaxy install -r requirements.yml
```
