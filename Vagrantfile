#!/usr/bin/env ruby
# frozen_string_literal: true

# mode: ruby -*-
# vi: set ft=ruby :

ENV['VAGRANT_DEFAULT_PROVIDER'] = 'virtualbox'

Vagrant.configure('2') do |conf|
  conf.vm.box = 'generic/alpine313'
  conf.vm.box_check_update = false
  conf.vm.provider :virtualbox do |v|
    v.memory = 512
    v.cpus = 1
    v.linked_clone = true
  end

  conf.vm.synced_folder 'caps/', '/home/vagrant/mnt'

  # Machine 1
  conf.vm.define 'alpine1' do |config|
    config.vm.hostname = 'alpine1'
    config.vm.network 'private_network',
                      ip: '192.168.112.2',
                      virtualbox__intnet: 'LabRedes1'
  end

  # Machine 2
  conf.vm.define 'alpine2' do |config|
    config.vm.hostname = 'alpine2'
    config.vm.network 'private_network',
                      ip: '192.168.112.3',
                      virtualbox__intnet: 'LabRedes1'
  end
end
