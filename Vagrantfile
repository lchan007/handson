# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
DOMAIN = '.dev'
boxes =[
  {
    :name => "ub18",
    :eth1 => "192.168.4.3",
    :mac1 => "000c295526e1",
    :mem  => "2048",
    :cpu  => "2",
  },
  {
    :name => "ce7",
    :eth1 => "192.168.4.4",
    :mac1 => "000c295526e3",
    :mem  => "2048",
    :cpu  => "2",
  }
]
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.provider "virtualbox" do |vb|
  config.vm.synced_folder "~/.ssh/", "/root/.ssh/",
    owner: "root", group: "root"
  vb.customize ["modifyvm", :id, "--memory", "1024"]
  # http://www.virtualbox.org/manual/ch09.html#nat-adv-dns
  vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
  vb.memory = 1024
  vb.cpus = 2
  vb.linked_clone = true
  
  end

  boxes.each do |opts|
    config.vm.define opts[:name] do |config|
      config.vm.hostname = opts[:name] + DOMAIN
      config.vm.network :private_network, ip: opts[:eth1]
      config.vm.provider "virtualbox" do |vb|
        vb.customize ["modifyvm", :id, "--macaddress1", opts[:mac1]]
        vb.memory = opts[:mem]
        vb.cpus = opts[:cpu]
      end
    end
  end

$script = <<-SCRIPT
function setup_ansible(){
  useradd -m -u 8000 -s /bin/bash ansible || return
  echo '%ansible ALL=(ALL) NOPASSWD: ALL' > /etc/sudoers.d/ansible
  mkdir /home/ansible/.ssh
cat <<-KEY_STRING >> /home/ansible/.ssh/authorized_keys
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC6uTNNlucIsgpugqmJYX3pMtr9oqK3kB5bDnwo0hWAeILqU/z9iSUKorq9DoK4fRzgXs15+v+oPJIWsg3lTLUxASBoVbkNcM7Y+Tne1TIyxgmYa69Uo2sUrrSXBtURX5u+/DcRkYovzqH9M/dFHoHSehDajFer0smX9KQRNDeZeTpTNf6VM6P99QcV4nt9X5eCstupYxsyHiMnaITVxNiKKquiehw07bj9ekIZjX6fjY2+lHDf+DkrFxZ7Q5P22wEaGY6UF+diOOVGS8AtFjnPx8dz0QJjDQVYYXyB//ap5eIzLe/7GWiX+Dhiim64/0tCf5iPQ48Njr+35kRSWEiD ka.chan@raq10-574.local
KEY_STRING
  chmod 0700 /home/ansible/.ssh
  chmod 0600 /home/ansible/.ssh/authorized_keys
  chown -Rv ansible.ansible /home/ansible/.ssh
  ping -c 1 8.8.8.8 >/dev/null && apt-get install python-apt curl -y || echo 'No internet access?'
}
setup_ansible
SCRIPT

config.vm.define "ub18" do |device|
    device.vm.hostname = "ub18"
    device.vm.box = "ubuntu/bionic64"
    config.vm.provision "shell", inline: $script
end
config.vm.define "ce7" do |device|
    device.vm.hostname = "ce7"
    device.vm.box = "centos/7"
end

end
