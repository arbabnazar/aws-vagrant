Use Vagrant to launch Amazon EC2 Instance
----
There's a blog post that I wrote to go along with this. [Check it out!]

This simple vagrant file helps you to create an EC2 instance on AWS.

I am assuming that you already have Vagrant installed and have an AWS account(and know how to use both).

First you need to install the Vagrant AWS plugin:
```bash
vagrant plugin install vagrant-aws
```
After installing the plugin, add dummy AWS box: 
```bash
vagrant box add aws https://github.com/mitchellh/vagrant-aws/raw/master/dummy.box
```

Next login to your AWS console to get the following things:

- AWS access key
- AWS secret key
- Security Group name (Make sure that security group enables the SSH port (22) from anywhere)
- SSH private key file, which will be in .pem extension

I like to set up these parameters as environment variables so that I'll keep them out of the Vagrantfile. On Linux/MAC, you can add them to ~/.profile file:
```bash
export AWS_ACCESS_KEY="ABCABCABCABCABCABC" 
export AWS_SECRET_KEY="HHRDDDDDDDDDDDDYYYYYYYYYYFFFFFFFFFFKKKK"
export AWS_PRIVATE_KEY="/Users/arbab/KEYS/vagrant.pem"
```

After that use the provided Vagrantfile. In this file, I have all the basic AWS-related settings, please refer to the [vagrant-aws documentation] for detail options. 

And then run by specifying the AWS plugin as the provider:
```bash
vagrant up --provider=aws
```

This will launch an `Ubuntu 14.04` instance in the `us-east-1` region within your account. If you have issues with SSH connecting, make sure that the SSH access is allowed in the security group of launched instance.
[vagrant-aws documentation]:https://github.com/mitchellh/vagrant-aws
[Check it out!]:https://rbgeek.wordpress.com/2015/02/19/provision-configure-ec2-instance-with-vagrant-and-ansible/
