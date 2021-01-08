# Personalized AT&T Ubuntu VM:
A vagrant script for setting up a personalized at&t ubuntu VM.

## Pre-requisites

 * **[Vagrant 2.1.4+](https://www.vagrantup.com)**
 * **[Virtualbox 5.2.18+](https://www.virtualbox.org)**
 * **[Git for Windows](https://git-scm.com/downloads)**

## Note
1) All the Vagrant and Git commands should be run from Git Bash.

2) You need to edit the servers array in the Vagrantfile to provide your customized mandatory inputs.

```
servers = [
    {
        :name => "zdsvtxlocnc01",
        :box => "ubuntu/xenial64",
        :box_version => "20180831.0.0",
        :mem => "2048",
        :cpu => "2",
        :attuid => "<attuid>",                #<AlphaNumeric attuid>
        :add_id_rsa => "true",
        :attname => "<FirstName LastName>",   #<FirstName LastName>
        :attpassword => "<Login Password>",   #<Login Password into VM>
        :uid => "<attUID>",                   #<Numeric attUID>
        :attgroup => "<attGroupName>",        #<Alphabetic attGroupName>
        :gid => "<attGID>",                   #<Numeric attGID>
        :gerrit_url => "<Gerrit Server FQDN>",#<Gerrit Server FQDN>
        :gerrit_repos => "<Gerrit Repos to be cloned>", #<Gerrit Repos to be cloned(seperated by commas)>
    }
]

```

## add_id_rsa:
If set to true, You need to create id_rsa file with your private key in the same folder of your Vagrantfile.

As you can see above, you can also configure memory and CPU in the servers array. 

## How to Run

Execute the following vagrant command to start provisioning of VM in the same folder of your Vagrantfile:

```
vagrant validate

vagrant up
```

##Connect/Access To VM

Check th VM status using vagrant.
```
vagrant status
Current machine states:

zdsvtxlocnc01                running (virtualbox)

This environment represents multiple VMs. The VMs are all listed
above with their current state. For more information about a specific
VM, run `vagrant status NAME`.
```

List the Host to Guest Ports.
```
vagrant port zdsvtxlocnc01
The forwarded ports for the machine are listed below. Please note that
these values may differ from values configured in the Vagrantfile if the
provider supports automatic port collision detection and resolution.

    22 (guest) => 2200 (host)
```

Connect to VM using localhost(You can also use Putty/Mobaxterm).

#Note: Default LoginUser/Password: vagrant/vagrant
#      Custom  LoginUser/Password: <attuid>/<Login Password> defined in above Servers block(Recommended).
```
ssh -p 2200 localhost -l vagrant
           (or)
ssh -p 2200 localhost -l <USERID>
```

## Clean-up

Execute the following command to remove the virtual machines created for the Kubernetes cluster.
```
vagrant destroy -f zdsvtxlocnc01

vagrant status
```

## Licensing

[Apache License, Version 2.0](http://opensource.org/licenses/Apache-2.0).
