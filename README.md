# The Railsbridge Boston Virtual Machine

This is a new setup method for Railsbridge Boston workshop.

Set up all the software you need by following these steps:

1. Download and install [VirtualBox][vbox]

[vbox]:https://www.virtualbox.org/wiki/Downloads

2. Download and install [Vagrant][vagrant]

[vagrant]:http://downloads.vagrantup.com/tags/v1.2.7

3. Download the [Railsbridge Boston Virtual machine][rbbvm] with this command:

    vagrant box add railsbridgebos http://66.228.42.213/railsbridgebos.box

[rbbvm]:vagrant box add lucid32 http://files.vagrantup.com/lucid32.box

4. Change directory into a workspace for your Railsbridge tutorial, and start
   your machine!

    vagrant up
    vagrant ssh

5. Stop your machine with

    vagrant halt

More instructions to be added later. This is just a first cut!





