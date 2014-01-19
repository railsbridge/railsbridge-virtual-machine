# The Railsbridge Virtual Machine

![img](https://raw.github.com/railsbridge-boston/railsbridge-virtual-machine/master/vm.png)

The Railsbridge Virtual Machine simplifies and standardizes the set up process
for Railsbridge introductory workshops. This method works on many [guest
OSes](https://www.virtualbox.org/wiki/Guest_OSes). 

The Railsbridge VM provides a faster and more reliable way to set up different
computers for Railsbridge. The manual alternative involves installing Xcode,
RVM/rbenv/chruby, etc. manually. This manual process is slower, more
bandwidth-intensive, and more error-prone.  And unlike
[RailsInstaller](http://railsinstaller.org/en), the Railsbridge Virtual Machine
can be tweaked to support the latest version of Rails.

Note for workshop participants:

The virtual machine creates a "computer within your computer", fully loaded
with the software you need to run Ruby and Rails programs, plus the tools to
deploy it on the Internet with Heroku and save changes in Git source control.

Set up all the software you need (except for the text editor) by following these steps:

Note: The current RailsBridge VM has been verified with Vagrant 1.2.7, which requires VirtualBox 4.2 .

## Step 1. 

Download and install [VirtualBox 4.2][vbox] . 

[vbox]:https://www.virtualbox.org/wiki/Download_Old_Builds_4_2

## Step 2. 

Download and install [Vagrant 1.2.7][vagrant]

[vagrant]:http://downloads.vagrantup.com/tags/v1.2.7

## Step 3.

Open a command prompt. See the [Using the Command Prompt Lab][command_prompt] , for a refresher on how to start the command prompt. 

[command_prompt]:http://www.railsbridgeboston.org/installfest/command_prompt
Download the Railsbridge Boston Virtual Machine with this command:

For Rails 3.2 and Ruby 1.9.3:

    vagrant box add railsbridgebox http://s3.amazonaws.com/railsbridgeboston/railsbridgevm-3.2-c.box


For Rails 4.0 and Ruby 2.0:

    vagrant box add railsbridgebox http://s3.amazonaws.com/railsbridgeboston/railsbridgevm-4.0.box

Note for organizers: to prevent network overload, it's best to download the box image ahead of time and install from the file.   Point a web browser to the box URL and save it.  To install, use the 'file://' prefix, followed by the path to the file.

    vagrant box add railsbridgebox file://railsbridgevm-4.0.box


## Step 4. 

Create a workspace directory for your Railsbridge tutorial.

Go to your home directory:

    cd ~

Make a new directory for the workshop:

    mkdir workspace

Move into that directory:

    cd workspace

This directory will be shared between the virtual machine and your computer. Like sharing files between two real computers with Dropbox or Google Docs, files need to be saved in a place that both computers can see. Save all your work in the hands-on exercises here so they can be run in the virtual machine. 

## Step 5.

Create and start your machine!

This is a one-time step to create the virtual machine for the workshop.

    vagrant init railsbridgebox


Here is what you should see (approximately):

```
[choi@mini rbb]$ vagrant init railsbridgebox
A `Vagrantfile` has been placed in this directory. You are now
ready to `vagrant up` your first virtual environment! Please read
the comments in the Vagrantfile as well as documentation on
`vagrantup.com` for more information on using Vagrant.
```

Start the virtual machine:

    vagrant up

It will do something like this:
```
choi@mini rbb]$ vagrant up
Bringing machine 'default' up with 'virtualbox' provider...
[default] Importing base box 'railsbridgebox'...
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
```

Connect to the virtual machine and start a command prompt: 

    vagrant ssh

You will see:
```
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

We will walk through creating an SSH key, configuring git, and creating a Heroku account in the workshop.  They are one-time steps.

Run 'vagrant up' every time you start the virtual machine.

Run 'vagrant ssh' every time you connect to the virtual machine.

## Step 6. 
    
Do the workshop exercises. 
    
## Step 7.

Logout and stop your machine with

    logout
    vagrant halt

Here's some more info on [Vagrant commands](http://docs.vagrantup.com/v2/cli/index.html).

These instructions will be refined later. This is just a first cut.

## Image Digests

* SHA1 railsbridgevm-3.2-c.box = c3ac52a72d2d3ba92d4d50481e7d426937c59753
* SHA1 railsbridgevm-4.0.box = 293c4e052827bbbe265ba3b2e5436d67d510bb2e


## How to make a new Railsbridge VM

You can tweak an existing VM and repackage it into a new box. Follow
these instructions:

1. Follow all the above steps, but then customize the environment in the
   Vagrant shell to change and customize the VM.

2. Edit the /etc/motd which is shown right after vagrant ssh login.

3. Edit or create ~/CHANGELOG.txt to describe your changes.  This will leave a history so your VM users can understand how this image is different from the baseline distribution.

4. Zero out all the unused disk space in the VM with these commands:

    ```
    dd if=/dev/zero of=/EMPTY bs=1M
    rm -f /EMPTY
    ```
    
5. Exit the vagrant shell and vagrant halt it.

6. Make sure there is a Vagrantfile in the directory with this content:

    ```
    Vagrant.configure("2") do |config|
      config.vm.network :forwarded_port, guest: 3000, host: 3000
    end
    ```

7. Create the new package with this command. NAME is the name of the box
   you're creating, e.g. railsbridgevm-3.2.box:
   
   ```
   vagrant package --output NAME --vagrantfile Vagrantfile
   ```


## Sorry Chromebook users

Chromebooks are not supported. Chromebook users might want to use
[Nitrous.IO](http://nitrous.io/) for the Railsbridge workshop.





