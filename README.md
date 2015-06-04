SAIO Ansible playbook
=========

An Ansible playbook for provisioning a [Swift](http://docs.openstack.org/developer/swift/development_saio.html) and [Swift-on-File](https://github.com/stackforge/swiftonfile/blob/master/doc/markdown/quick_start_guide.md) all-in-one
development environment on Fedora or CentOS(default).

## To run:
To provision the VM, run:
 1. `vagrant up`

To run automated tests:
 1. `vagrant ssh`
 1. `cd /vagrant/source/swift`
 1. `tox -e py27`
 1. `tox -e func`

### Configuration Options:
You can set a few options to change how the VM is provisioned. In `global_vars.yml`, you can set if you want Swift-on-File configured or not and what storage policy should be set as the default. In the `Vagrantfile`, you can choose to provision either a Fedora VM or a CentOS-7 VM.

#### Gerrit repo setup
In case you would like to use the provisioned VM as your development environment, Ansible can add gerrit as a remote repo to both Swift and Swift-on-File. Checkout the options in `global_vars.yml`

### Running Ansible only:
In case you already have a VM created and just wants to execute the Ansible playbook, run the following command:
 1. `ansible-playbook site.yml -i "192.168.56.103," --ask-sudo-pass`

####Notes: 
 * Make sure to update to the correct IP address on the command above (it's important to keep the comma ',' at the end) and the `username` and `group` variables in `global_vars.yml`
 * If testing on RHEL/CentOS, enable EPEL repository first.

## Todo:
* Add gluster volume
