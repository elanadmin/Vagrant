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
## Licensing

[Apache License, Version 2.0](http://opensource.org/licenses/Apache-2.0).
