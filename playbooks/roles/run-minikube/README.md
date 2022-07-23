run-minikube
=========

Since [gantsign.minikube](https://galaxy.ansible.com/gantsign/minikube) only installs minikube, we need to
run it manually for:

- be able to deploy apps into it
- get a kubeconfig for it

...so, this role runs minikube

Requirements
------------

You need to install minikube first - for example, by [gantsign.minikube](https://galaxy.ansible.com/gantsign/minikube)

Role Variables
--------------

run_dashboard - set to true if you want to run k8s dashboard

Dependencies
------------

Consider using this role with [gantsign.minikube](https://galaxy.ansible.com/gantsign/minikube) in order to install
ans run minikube with ansible only

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - run-minikube

License
-------

BSD

Author Information
------------------

Savin Andrey andrei.v.savin@gmail.com
