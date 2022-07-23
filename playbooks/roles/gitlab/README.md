Gitlab
=========

Role for installing self-hosted gitlab version to k8s cluster using helm

Requirements
------------

PyYAML
Helm
Valid kubeconfig

Role Variables
--------------

namespace - kubernetes namespace to install Gitlab
gitlab_domain - local domain wich will be used for generations level 3 domains for Gitlab installation

Dependencies
------------

none

Example Playbook
----------------

    - hosts: servers
      roles:
        - role: gitlab

License
-------

BSD

Author Information
------------------

Savin Andrey andrei.v.savin@gmail.com
