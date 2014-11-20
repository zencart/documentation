Customising Habitat
===========

When habitat first creates the development environment, it looks for a file called Habitat.local.yaml, which it will use to provision you Virtual Machine.

If Habitat.local.yaml does not exist, it will copy the included Habitat.yaml.example to Habitat.local.yaml

By default the example file will do a checkout of the latest v160 branch from Github. If you want that checkout to say be your forked branch, then you will need to create the Habitat.local.yaml first.

`Note` If you make changes to the yaml file after doing Vagrant up, you will need to run ...
>
`Command Line`  
>
vagrant provision

in order for the changes to take affect.

The options are.

### ip:

This is the ip that is assigned to your virtual machine. You should only change it if the current IP clashes with settings on your local machine/network
If assigning a new IP address, you should not use a publicly available IP, but an IP from one of the private IP spaces.

###memory:

The amount of memory assigned to your virtual machine.

###cpus:

The number of cpu cores assigned to your virtual machine.
do_default_map:

This can be true or false. In the default yaml file it is set to true, and controls whether to share the internal habitat directory with the host machine.

There is little reason to change this setting unless you have advanced knowledge of managing a vagrant virtual machine.
###sites:

This option can be used create other virtual domains that map to a directory and optionally clone a github repository into that directory

By default it contains :-

                sites:
                  - skeleton: apache.default
                    domain: zen.local
                    dir: zen
                    github: https://github.com/zencart/zc-v1-series.git
                    branch: v160
              

If you want to add another site, you can do

                sites:
                  - skeleton: apache.default
                    domain: zen.local
                    dir: zen
                    github: https://github.com/zencart/zc-v1-series.git
                    branch: v160
                  - skeleton: apache.default
                    domain: v150.local
                    dir: v150
                    github: https://github.com/zencart/zc-v1-series.git
                    branch: v150-release
            

The options within the sites directive are :-
####skeleton:

In order to provision apache correctly, we use a skeleton vhosts file.

These skeleton files are stored in the shared scripts/skeletons directory.

There are currently only two skeleton files (apache.default and nginx.default). However others may be made available, or you may want to create your own.
####domain:

This is the name of the domain that you want to map to your shared site. Currently, you will also have to create an entry in your hosts files for the domain.
####dir:

This is the directory, relative to the shared habitat/web directory, that you want to be the web root of your site.
####github:

This directive is optional, but if set will be used as the repository to clone.
branch:

This directive is optional, but if set will be used as the branch to checkout.



