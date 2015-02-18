# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "aws"
  config.vm.synced_folder ".", "/vagrant", disabled: true

  config.vm.provider :aws do |aws, override|
	  aws.access_key_id = ENV['AWS_ACCESS_KEY']
	  aws.secret_access_key = ENV['AWS_SECRET_KEY']
	  aws.region = "us-east-1"
	  aws.availability_zone = "us-east-1c"

	  # AMI from which we'll launch EC2 Instance
	  aws.ami =  "ami-9a562df2" # Ubuntu 14.04
	  aws.keypair_name = "vagrant"
	  aws.instance_type = "t2.micro"
	  aws.block_device_mapping = [{ 'DeviceName' => '/dev/sda1', 'Ebs.VolumeSize' => 10 }]
	  aws.security_groups = ["vagrant-sg"]
          aws.tags = {
		        'Name' => 'Vagrant EC2 Instance',
		  	'Environment' => 'vagrant-sandbox'
		     }  
          # Credentials to login to EC2 Instance
	  override.ssh.username = "ubuntu"
	  override.ssh.private_key_path = ENV['AWS_PRIVATE_KEY']
  end

end
