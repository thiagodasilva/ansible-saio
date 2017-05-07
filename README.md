SAIO Ansible playbook
=========

An Ansible playbook for provisioning a [Swift](http://docs.openstack.org/developer/swift/development_saio.html) and [Swift-on-File](https://github.com/openstack/swiftonfile/blob/master/doc/markdown/quick_start_guide.md) all-in-one
development environment on CentOS.

## Requirements:
The CentOS 7 image being used by default does not have the VirtualBox Guest Additions preinstalled. Install the vagrant-vbguest plugin to have it installed on your guest VM automatically.
 1. `vagrant plugin install vagrant-vbguest`

## To run:
To provision the VM, run:
 1. `vagrant up --provider=virtualbox`

To run automated tests:
 1. `vagrant ssh`
 1. `cd /vagrant/source/swift`
 1. `./.unittests`
 1. `./.functests`

To quickly test installation:
 1. `swift stat`
 1. `echo 'hello world' > hw`
 1. `swift upload c1 hw`
 1. `swift list`

To test installation with Swift-on-File (Note: make sure to have Swift-on-File provisioned):
 1. `swift post c2 -H 'X-Storage-Policy: swiftonfile'`
 1. `echo 'hello swiftonfile' > hs`
 1. `swift upload c2 hs`
 1. `swift list`
 1. `ls /mnt/swiftonfile`

### Configuration Options:
You can set a few options to change how the VM is provisioned. In `global_vars.yml`, you can set if you want Swift-on-File configured or not and what storage policy should be set as the default.

#### Hummingbird setup
To test the hummingbird branch; in `global_vars.yml`, set `configure_hummingbird` to `yes` before running `vagrant up`. Once vagrant is done provisioning, run the following:
 1. `vagrant ssh`
 1. `cd go_work/src/github.com/openstack/swift/go`
 1. `make get test all`
 1. `startmain`
 1. `swift upload c1 hw`
 1. `swift list`

#### Gerrit repo setup
In case you would like to use the provisioned VM as your development environment, Ansible can add gerrit as a remote repo to both Swift and Swift-on-File. Checkout the options in `global_vars.yml`

### Running Ansible only:
In case you already have a VM created and just wants to execute the Ansible playbook, run the following command:
 1. `ansible-playbook site.yml -i "192.168.56.103," --ask-sudo-pass`

#### Notes:
 * Make sure to update to the correct IP address on the command above (it's important to keep the comma ',' at the end) and the `username` and `group` variables in `global_vars.yml`
 * If testing on RHEL/CentOS, enable EPEL repository first.

## Todo:
* Add gluster volume
