---
title: Setting Up a Vagrant Box for Virtual Development
date: "2020-02-18T11:32:32.169Z"
description: Tutorial for starting a vagrant virtual box and test bed for web development.
---

Working on a virtual machine has many benefits for web developers. It gives access to linux for Windows and Mac users but more importantly it allows for reliable and standardized porting for tailored distributions.

With Vagrant developers can utilize these benefits as well as easily host local builds on development boxes.



Here is how to get one running:
---
---

1. Installation

[Download](https://www.vagrantup.com/downloads.html) the vagrant installer for your specific operating system and follow the perscribed installation procedures.

Vagrant should now be installed. To test that `vagrant` was successfully installed:
```
$ vagrant
Usage: vagrant [options] <command> [<args>]

    -v, --version                    Print the version and exit.
    -h, --help                       Print this help.
```
---

2. Creating a Vagrantfile

Now that Vagrant is installed make a new directory for your project's files.

```
$ mkdir my-project
$ cs my-project
```

Now that we have this directory we need to make a Vagrantfile to initialize Vagrant and to store information between sessions.

At this point we need to choose the operating system that Vagrant will run. [This list](https://app.vagrantup.com/boxes/search) contains all boxes on Vagrant's platform but I will be using `ubuntu/bionic64` which is the Ubuntu 18.04 LTS operating system.

```
$ vagrant init ubuntu/bionic64
```

*Note: Be sure to interchange your preferred box in the init command*

This will generate a file named `Vagrantfile`.

---

3. Starting and Connecting to your VM

Now your Vagrantfile is in place starting the virtual machine is as simple as:

```
$ vagrant up
```

On the first run (or any subsequent change of os/reinstall) this will take a while to initialize since it has to install the entire operating system. Subsequent launches should be much quicker.

Once `vagrant up` completes type:

```
$ vagrant ssh
```

Now you will be connected to the virtual box.

---

4. Exiting and Relaunching

Once you are done developing you can type `logout` to exit back to your normal terminal window.

*Note: Vagrant will still be running and you can reconnect with* `vagrant ssh` *immediately.*

To shut down the VM temporarily use:

```
$ vagrant suspend
```

To start the VM back up use:

```
$ vagrant up
```

If you want to fully delete the installation of the VM along with all data contained use:

```
$ vagrant destroy
```

---

Once you have your own Vagrant box you can develop just like any other linux machine and host builds locally. Hopefully this helps with the installation procedure.