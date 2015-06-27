# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.box       = 'openstack'
  config.ssh.username = 'cloud-user'
  config.ssh.pty      = true

  require 'vagrant-openstack-provider'
  config.vm.provider :openstack do |os, override|
    os.username               = ENV['OS_USERNAME']
    os.password               = ENV['OS_PASSWORD']
    os.tenant_name            = ENV['OS_TENANT_NAME']
    os.flavor                 = 'm1.small'
    os.image                  = 'centos-6.5-20140117.0'
    os.networks               = ENV['OS_INTERNAL_NETWORK']

    os.openstack_auth_url     = "#{ENV['OS_AUTH_URL']}/tokens"
    os.openstack_network_url  = ENV['OS_NETWORK_URL']
    os.openstack_image_url    = ENV['OS_IMAGE_URL']
    os.availability_zone      = ENV['OS_AVAILABILITY_ZONE']
    os.floating_ip_pool       = ENV['OS_EXTERNAL_NETWORK']
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook =  "site.yml"
  end
end
