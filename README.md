# The Railsbridge Boston Virtual Machine

![img](https://raw.github.com/railsbridge-boston/railsbridge-virtual-machine/master/vm.png)

This is a proposed new setup method for the Railsbridge Boston workshop. It
could mean bye bye Xcode, RVM, rbenv, and Windows installfest headaches. 

Set up all the software you need (except for the text editor) by following these steps:

## Step 1. 

Download and install [VirtualBox][vbox]

[vbox]:https://www.virtualbox.org/wiki/Downloads

## Step 2. 

Download and install [Vagrant][vagrant]

[vagrant]:http://downloads.vagrantup.com/tags/v1.2.7

## Step 3. 

Download the [Railsbridge Boston Virtual Machine][vm] (579MB) with this command:

    vagrant box add railsbridgebos http://66.228.42.213/railsbridgebos.box

[vm]:http://66.228.42.213/railsbridgebos.box

## Step 4. 

Change directory into a workspace for your Railsbridge tutorial, and start
your machine!

    vagrant init railsbridgebos
    vagrant up
    vagrant ssh

Here is what you should see (approximately):

```
[choi@mini rbb]$ vagrant init railsbridgebos
A `Vagrantfile` has been placed in this directory. You are now
ready to `vagrant up` your first virtual environment! Please read
the comments in the Vagrantfile as well as documentation on
`vagrantup.com` for more information on using Vagrant.
choi@mini rbb]$ vagrant up
Bringing machine 'default' up with 'virtualbox' provider...
[default] Importing base box 'railsbridgebos'...
[default] Matching MAC address for NAT networking...
[default] Setting the name of the VM...
[default] Clearing any previously set forwarded ports...
[default] Creating shared folders metadata...
[default] Clearing any previously set network interfaces...
[default] Preparing network interfaces based on configuration...
[default] Forwarding ports...
[default] -- 22 => 2222 (adapter 1)
[default] -- 3000 => 3000 (adapter 1)
[default] Booting VM...
[default] Waiting for VM to boot. This can take a few minutes.
[default] VM booted and ready for use!
[default] Configuring and enabling network interfaces...
[default] Mounting shared folders...
[default] -- /vagrant
[choi@mini rbb]$ vagrant ssh
Welcome to Ubuntu 12.04 LTS (GNU/Linux 3.2.0-23-generic-pae i686)

 * Documentation:  https://help.ubuntu.com/

Welcome to the Railsbridge Boston virtual machine!

Everything you need for the Suggestotron tutorial is installed, including:

- Ruby 2.0
- Rails 4.0
- sqlite3
- heroku toolbelt
- git

Next steps:

1. Create a SSH key
2. Configure Git
3. Create a Heroku account

The ~/workspace directory from inside the VM shell is identical to the host
directory of your VM workspace.

When you start your Rails app, visit http://localhost:3000 in your web browser.

Last login: Tue Aug 27 00:38:27 2013 from 10.0.2.2
vagrant@precise32:~$ 
```


## Step 5. 
    
Do your stuff.
    
## Step 6.

Logout and stop your machine with

    logout
    vagrant halt

Here's some more info on [Vagrant commands](http://docs.vagrantup.com/v2/cli/index.html).

These instructions will be refined later. This is just a first cut.


## Future improvements

* Put the Railsbridge Boston Virtual Machine download on S3 and/or torrents. Right now it's on a slow server for downloading.
* Put all installers and VM on USB keys. Figure out total space required.
* Test on all likely laptop models and operating systems. AMD CPUs may be an edge case.




