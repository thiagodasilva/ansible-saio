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

### Running ansible only:
In case you already have a VM created and just wants to execute the ansible playbook, run the following command:
 1. `ansible-playbook site.yml -i "192.168.56.103," --ask-sudo-pass`

####Notes: 
 * Make sure to update to the correct IP address on the command above (it's important to keep the comma ',' at the end) and the `username` and `group` variables in `site.yml`
 * If testing on RHEL/CentOS, enable EPEL repository first.

## Todo:
* Add Swift-on-File storage policy
* Add ability to provide gerrit ssh keys and setup `git review`

