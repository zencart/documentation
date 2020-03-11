---
title: Customizing Habitat
weight: 4
---

Customising Habitat
===========

When Habitat first creates the development environment, it looks for a file called Habitat.yaml, which it will use to provision you Virtual Machine.

If `Habitat.yaml` does not exist, it will copy the included `Habitat.yaml.example` to `Habitat.yaml`

By default the example file will do a checkout of the latest develop branch from Github. If you want that checkout to say be your forked branch, then you will need to create the Habitat.yaml first and adjust it to point to your own forked repo instead of the github.com/zencart repo.

**Note** If you make changes to the yaml file after doing `Vagrant up`, you will need to run ...
>
`Command Line`  
>
vagrant provision

in order for the changes to take affect.


Habitat.yaml Configuration Options
==================================

The configuration options for the YAML file are as follows. NOTE: Some of these are NOT shown in the example file.

###hostname:

This defaults to `habitat`. If you want to rename the machine to differentiate multiple instances (as they show up in VirtualBox), you can set this here.

Normally best left as-is, or skipped altogether.

###ip:

This is the ip that is assigned to your virtual machine. You should only change it if the current IP clashes with settings on your local machine/network
If assigning a new IP address, you should not use a publicly available IP, but an IP from one of the private IP spaces.

The default is `172.22.22.22`

###memory:

The amount of memory assigned to your virtual machine.

The default is `1024`

###cpus:

The number of cpu cores assigned to your virtual machine.

The default is `1`


###sites:

This option can be used create other virtual domains that map to a directory and optionally clone a github repository into that directory

By default it contains:

                sites:
                  - domain: zen.local
                    dir: develop
                    skeleton: apache.default
                    git_url: https://github.com/zencart/zencart.git
                    branch: develop
                  - domain: devdocs.local
                    dir: devdocs
                    skeleton: apache.default
                    git_url: https://github.com/zencart/documentation.git
                    branch: master
              

If you want to add another site, you can add something like:

                  - domain: v154.local
                    dir: v154
                    skeleton: apache.default
                    git_url: https://github.com/zencart/documentation.git
                    branch: v154
            

The options within the `sites:` directive are:

####domain:

This is the name of the domain that you want to map to your shared site. You will also have to create an entry in your `hosts` file for this same domain.

####dir:

This is the directory, relative to the shared Habitat/web directory, that you want to be the web root of your site.

See `do_default_map:` and `to:` below for more info.

####skeleton:

In order to provision apache correctly, we use a skeleton apache vhost file.

These skeleton files are stored in the shared scripts/skeletons directory.

Currently only the `apache.default` skeleton is used.

####git_url:

This directive is optional, but if set will be used as the repository to clone. It is typical to use a github.com or bitbucket.org URL here, for example: `https://github.com/zencart/zencart.git`

####branch:

This directive is optional, but if set will be used as the branch to checkout, in reference to the `git_url` directive.

####docroot:

This directive is optional, but if you need to override or set a different document-root (ie: re-point to a subdir like 'public') set that by adding this directive. For example: `docroot: /public`

###do_default\_map:

This controls whether to share the internal Habitat directory with the host machine.

The default is true. There is little reason to change this setting unless you have advanced knowledge of managing a vagrant virtual machine.

###folders:

The default mapping is to map the `map:` folder from your host PC to the `to:` folder in your VM. If `create:` is set to `true` then it will also create the folder on both ends if it doesn't already exist.

####map:

The local PC folder where files are stored on your PC. These files will be synced into the `to:` folder of the vm, and vice-versa.

The default is assumed to be the local folder from which you're running vagrant/habitat.

####to:

This is the name of the folder inside vagrant/habitat which the files from the `map:` folder will be synced to/from the vm.

The default is `/home/vagrant/web`, and the `dir:` directive will be put inside this folder.

####create:

This determines whether to create the folder automatically if it doesn't already exist.  

The default is true.


###authorize:

This can be used to specify which RSA public key file you want copied to the vm for easy login from your host machine's command-line if you don't want to use the default `vagrant ssh` command. See the vagrantup.com documentation for more detail.

###keys:

This is a list of private RSA keys you want copied to the VM. This can be useful if you're having any difficulty connecting to github or bitbucket due to private-key problems. 

###localize_tools:

This determines whether to map the vm's `/tools` folder to your host machine. This is required (useful) to run the supplied unittesting tools. See the [Tools](dev-tools) documentation.

The default is `true`

