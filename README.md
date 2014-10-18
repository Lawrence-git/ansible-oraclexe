ansible-oraclexe
================

#Ansible playbook for oracle-xe

This is an [Ansible](http://www.ansibleworks.com/) playbook for [Oracle XE 11g](http://www.oracle.com/technetwork/products/express-edition/overview/index.html). You can use it by itself or as part of a larger playbook customized for your local environment.

Prerequisites
-------------

You need to download Oracle XE 11g release 2 from [oracle](http://www.oracle.com/technetwork/products/express-edition/downloads/index.html) and add it under ./files directory.

Steps
-----

## Testing locally with Vagrant
A sample [Vagrant](http://www.vagrantup.com/) configuration is provided to help with local testing. After installing Vagrant, run `vagrant up` at the root of the project to get a VM instance bootstrapped and configured with a running instance of Oracle XE 11g.

## Include role in a larger playbook
### Add this role as a git submodule
Assuming your playbook structure is such as:
```
- my-master-playbook
  |- vars
  |- roles
  |- my-master-playbook-main.yml
  \- my-master-inventory.ini
```

Checkout this project as a submodule under roles:

```
$  cd roles
$  git submodule add git://github.com/fupelaqu/ansible-oraclexe.git ./ansible-oraclexe
$  git submodule update --init
$  git commit ./ansible-oraclexe -m "Added ansible-oraclexe as ./ansible-oraclexe"
```

### Include this playbook as a role in your master playbook
Example `my-master-playbook-main.yml`:

```
---

#########################
# Oracle XE install #
#########################

- hosts: dbservers
  user: ubuntu
  sudo: yes

  roles:
    - ansible-oraclexe

  vars_files:
    - vars/my-vars.yml
```

# Issues, requests, contributions
This software is provided as is. Having said that, if you see an issue, feel free to log a ticket. We'll do our best to address it. Same if you want to see a certain feature supported in the fututre. No guarantees are made that any requested feature will be implemented. If you'd like to contribute, feel free to clone and submit a pull request.

# Dependencies
None

# License
MIT

# Author Information

Stéphane Manciot - stephane.manciot [at] gmail.com
