---
title: Installing Habitat
weight: 2
---

Installation
============

Prerequisites
-------------

Install Virtualbox and Vagrant
>
`Ubuntu`
>
sudo apt-get install virtualbox  
sudo apt-get install vagrant
>
`Windows or Mac OSX`
>
https://www.virtualbox.org/wiki/Downloads  
https://www.vagrantup.com/downloads.html  

Install Habitat
---------------

Clone the habitat repository.
>
`Command Line`
>
git clone https://github.com/zencart/habitat  

Then change into the newly created habitat directory.

OPTIONAL: Add the Virtual Machine to Vagrant. (You don't have to do this manually. It will happen automatically for you.)
>
`Command Line`  
vagrant box add zencart/habitat https://s3.amazonaws.com/zencart-vagrant-boxes/habitat.box

Update your hosts file
>
`Ubuntu or Mac OSX`
>
/etc/hosts  
>
`Windows`
>
%systemroot%\system32\drivers\etc\hosts  
Where %systemroot% is usually c:/windows

And add this line
>
172.22.22.22 zen.local  
172.22.22.22 devdocs.local

Before you start up the VM you may want to customise the environment. If so see the [Customising](customising) page before starting the VM.

To start the VM:
>
`Command Line`
>
vagrant up
