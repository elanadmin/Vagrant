# Personalized Oracle VirtualBox VM:
A vagrant script for setting up a personalized Oracle VirtualBox VM.

## Pre-requisites

 * **[Vagrant 2.1.4+](https://www.vagrantup.com)**
 * **[Virtualbox 5.2.18+](https://www.virtualbox.org)**
 * **[Git for Windows](https://git-scm.com/downloads)**

## Note
1) All the Vagrant and Git commands should be run from Git Bash.
2) Navigate to the OS Version folders to launch specific OS VirtualBox VM's.
3) Please follow the README.md in OS folder for Specific instructions, You need to edit the servers array in the Vagrantfile to provide your customized mandatory inputs.

```
Example:

servers = [
    {
        :name => "edallocvm01",
        :box => "centos/7",
        :box_version => "2004.01",
        :mem => "2048",
        :cpu => "2",
	:eth1 => "192.168.205.13",
        :elanuser => "<USERID>",
        :add_id_rsa => "true",
        :username => "<USER FULLNAME>",
        :userpassword => "<USER PASSWORD>",
        :uid => "<UID>",
        :elangroup => "<GROUPID>",
        :gid => "<GID>",
        :os_codename => "maipo"
    }
]

```

## add_id_rsa:
If set to true, You need to create id_rsa file with your private key in the same folder of your Vagrantfile.

As you can see above, you can also configure IP address, memory and CPU in the servers array. 

## How to Run

Execute the following vagrant command to start provisioning of VM in the same folder of your Vagrantfile:

```
vagrant validate

vagrant up
```

## Access VM

Execute the following command to check status and access VM using vagrant:
```
vagrant status

vagrant ssh
```
(or)

Using Putty/Mobaxterm, you can access VM:
```
ssh 127.0.0.1 -p 2200
```

## Clean-up

Execute the following command to remove the virtual machines created for the Kubernetes cluster.
```
vagrant destroy -f
vagrant status
```

## Licensing

[Apache License, Version 2.0](http://opensource.org/licenses/Apache-2.0).
