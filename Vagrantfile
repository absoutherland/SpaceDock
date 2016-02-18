Vagrant.configure("2") do |config|
  config.vm.define "dcc" do |dcc|
    dcc.vm.box = "centos/7"
    dcc.ssh.forward_agent = true

    dcc.vm.network :private_network, ip: "10.10.10.25"

    dcc.vm.synced_folder ".", "/code",
      type: "nfs"

   dcc.vm.provider :virtualbox do |vb|
      vb.cpus = 2
      vb.memory = 1024
      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    end

    dcc.vm.provision :shell, inline: "curl -sSL https://get.docker.com/ | sh"
  end
end
