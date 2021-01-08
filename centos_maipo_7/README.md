# Personalized ELAN CentOS VM:
A vagrant script for setting up a personalized ELAN CentOS VM.

## Pre-requisites

 * **[Vagrant 2.1.4+](https://www.vagrantup.com)**
 * **[Virtualbox 5.2.18+](https://www.virtualbox.org)**
 * **[Git for Windows](https://git-scm.com/downloads)**

## Note
All the Vagrant and Git commands should be run from Git Bash.

You need to edit the servers array in the Vagrantfile to provide your customized mandatory inputs.

```
servers = [
    {
        :name => "edallocvm01",
        :box => "centos/7",
        :box_version => "2004.01",
        :mem => "2048",
        :cpu => "2",
        :elanuser => "<USERID>",       ##Alphabetic, example: rmoturi (ELAN members use same as your LDAP account userid).
        :add_id_rsa => "true",         ## id_rsa file with your openssh privatekey.
        :username => "<USER FULLNAME>",##Alphabetic, example: "Rajesh Moturi".
        :userpassword => "<PASSWORD>", ##Alphanumeric with special character are allowed (ELAN members use same as your LDAP account password).
        :uid => "<UID>",               ##Numeric, Any Number Between 50 and 500.
        :elangroup => "<GROUPID>",     ##Alphabetic, example: default.
        :gid => "<GID>",               ##Numeric, Any Number Between 50 and 500.
        :os_codename => "maipo"
    }
]

```

## add_id_rsa:
If set to true, You need to create id_rsa file with your private key in the same folder of your Vagrantfile.

As you can see above, you can also configure IP address, memory and CPU capacities in the servers array. 

## How to Run

Execute the following vagrant command to start provisioning of VM in the same folder of your Vagrantfile:

```
vagrant validate

vagrant up
```

## Select Network Interface:

Select the Network Interface for Bridge Adapter, When prompted:

```
==> edallocvm01: Available bridged network interfaces:
1) Intel(R) Dual Band Wireless-AC 7265
2) Microsoft Wi-Fi Direct Virtual Adapter #2
==> edallocvm01: When choosing an interface, it is usually the one that is
==> edallocvm01: being used to connect to the internet.
==> edallocvm01:
    edallocvm01: Which interface should the network bridge to? 1
```

##Connect/Access To VM

Check th VM status using vagrant.
```
vagrant status
Current machine states:

edallocvm01                running (virtualbox)

This environment represents multiple VMs. The VMs are all listed
above with their current state. For more information about a specific
VM, run `vagrant status NAME`.
```

List the Host to Guest Ports.
```
vagrant port edallocvm01
The forwarded ports for the machine are listed below. Please note that
these values may differ from values configured in the Vagrantfile if the
provider supports automatic port collision detection and resolution.

    22 (guest) => 2200 (host)
```

Connect to VM using localhost(You can also use Putty/Mobaxterm).

#Note: Default LoginUser/Password: vagrant/vagrant
#      Custom  LoginUser/Password: <USERID>/<PASSWORD> defined in above Servers block(Recommended).
```
ssh -p 2200 localhost -l vagrant
           (or)
ssh -p 2200 localhost -l <USERID>
```

## Clean-up

Execute the following command to remove the virtual machine.

```
vagrant destroy -f edallocvm01
```

You can destroy individual machines by vagrant destroy <VM> -f

## Licensing

[Apache License, Version 2.0](http://opensource.org/licenses/Apache-2.0).
