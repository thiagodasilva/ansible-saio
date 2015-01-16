SAIO Ansible playbook
=========

An Ansible playbook for provisioning a swift all-in-one development environment.
Based on the steps described here: http://docs.openstack.org/developer/swift/development_saio.html

## To run:
Before running, you will need to provision your own VM and update the `inventory` file with the IP address of the VM. Also, update the `username` and `group` variables in `site.yml`

Now, run:
~~~
ansible-playbook site.yml -i inventory --ask-sudo-pass
~~~

## Todo:
* Provide Vagrant file to provision VM
* Add Swift-on-File storage policy
* remove need for `--ask-sudo-pass`
* Add ability to provide gerrit ssh keys and setup `git review`

