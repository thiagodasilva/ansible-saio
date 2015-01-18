SAIO Ansible playbook
=========

An Ansible playbook for provisioning a swift all-in-one development environment
on Fedora. Based on the steps described here: http://docs.openstack.org/developer/swift/development_saio.html

## To run:
To provision the VM, run:
1. `vagrant up`

To run automated tests:
1. `vagrant ssh`
1. `cd swift`
1. `tox -e py27`
1. `tox -e func`

## Todo:
* Add Swift-on-File storage policy
* Add ability to provide gerrit ssh keys and setup `git review`

