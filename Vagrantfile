Vagrant.configure(2) do |config|
  config.vm.box = "chef/centos-7.0"
  #config.vm.box = "chef/fedora-20"
  VMS = 1
  (0..VMS-1).each do |vm|
    config.vm.define "server#{vm}" do |g|
        g.vm.hostname = "server#{vm}"
        g.vm.network :private_network, ip: "192.168.56.13#{vm}"

        if vm == (VMS-1)
            g.vm.provision :ansible do |ansible|
                ansible.playbook = "site.yml"
                ansible.groups = {
                    "storage" => (0..VMS-1).map { |v| "server#{v}" }
                }
                ansible.limit='all'
            end
        end
    end
  end
end
