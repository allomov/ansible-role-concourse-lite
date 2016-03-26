# Install concourse-lite easily on your host

![travis.ci status](https://travis-ci.org/allomov/ansible-role-concourse-lite.svg)

### Description

["Concourse-lite"](https://github.com/concourse/concourse-lite) is a simple way to install and manage [concouse.ci](http://concouse.ci/) on one VM. It uses vagrant and can install concourse to virtualbox or AWS.

Resulting machine contains all needed software to manage concourse-lite.

### Warning

This role is tested only on phisical machines, since it use virtualbox and it requires nested virtualization for your IaaS.

### Requirements

Install Ansible `2.0+`, you can use [this](http://docs.ansible.com/ansible/intro_installation.html) instruction or install ansible using `pip` (the following example installs Ansible to fresh Ubuntu):
```
sudo apt-get update
sudo apt-get install python-pip python-dev -y
sudo pip install ansible
```

### How to use

You will need to install the role, create 2 files and run one command:

```bash
ansible-galaxy install allomov.concourse-lite

cat <<EOF > playbook.yml
---
- hosts: jumpbox
  roles: 
  - role: allomov.bosh-jumpbox
EOF

cat <<EOF > hosts
[jumpbox]
localhost ansible_connection=local
EOF

ansible-playbook -i hosts playbook.yml
```

Enjoy!
