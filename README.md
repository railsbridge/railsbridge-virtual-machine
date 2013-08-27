# The Railsbridge Boston Virtual Machine

![img](https://raw.github.com/railsbridge-boston/railsbridge-virtual-machine/master/vm.png)

This is a new setup method for Railsbridge Boston workshop.

Set up all the software you need by following these steps:

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


## Step 5. 
    
    Do your stuff.
    
## Step 6.

Stop your machine with

    vagrant halt

These instructions will be refined later. This is just a first cut.


## Future improvements

* Make a Torrent out of the Vagrant box.
* Put all installers and VM on USB keys. Figure out space required.
* Test on all likely laptop models. AMD CPUs may be an edge case.




