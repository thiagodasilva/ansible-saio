SAIO Ansible playbook
=========

An Ansible playbook for provisioning a swift all-in-one development environment.
Based on the steps described here: http://docs.openstack.org/developer/swift/development_saio.html

## To run:
Currently, you will need to provision your own VM and update the file
`inventory` with the IP address of the VM, then run:
~~~
ansible-playbook site.yml -i inventory --ask-sudo-pass
~~~

## Todo:
* Provide Vagrant file to provision VM
* Add Swift-on-File storage policy
* Add ability to provide gerrit ssh keys and setup `git review`

