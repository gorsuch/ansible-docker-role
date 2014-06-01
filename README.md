ansible-docker-role
===================

An ansible playbook to mutate an Ubuntu Trusty box into a  docker host.

Includes a working Vagrant demo so you can see it in action.  

Includes Serverspec tests.

## Demo

First, startup the Vagrant box.  This will execute the playbook:

```sh
$ vagrant up
Bringing machine 'default' up with 'virtualbox' provider...
==> default: Importing base box 'thoughtbot/ubuntu-14-04-server'...
==> default: Matching MAC address for NAT networking...
==> default: Checking if box 'thoughtbot/ubuntu-14-04-server' is up to date...
==> default: Setting the name of the VM: ansible-docker-host_default_1401637754660_4670
==> default: Fixed port collision for 22 => 2222. Now on port 2202.
==> default: Clearing any previously set network interfaces...
==> default: Preparing network interfaces based on configuration...
    default: Adapter 1: nat
==> default: Forwarding ports...
    default: 22 => 2202 (adapter 1)
==> default: Booting VM...
==> default: Waiting for machine to boot. This may take a few minutes...
    default: SSH address: 127.0.0.1:2202
    default: SSH username: vagrant
    default: SSH auth method: private key
    default: Warning: Connection timeout. Retrying...
==> default: Machine booted and ready!
==> default: Checking for guest additions in VM...
==> default: Setting hostname...
==> default: Mounting shared folders...
    default: /vagrant => /Users/gorsuch/src/ansible-docker-host
==> default: Running provisioner: ansible...

PLAY [all] ******************************************************************** 

GATHERING FACTS *************************************************************** 
ok: [default]

TASK: [docker.io apt key] ***************************************************** 
changed: [default]

TASK: [docker.io repository] ************************************************** 
changed: [default]

TASK: [install docker] ******************************************************** 
changed: [default]

PLAY RECAP ******************************************************************** 
default                    : ok=4    changed=3    unreachable=0    failed=0   
```

Then, fire up your first docker container:

```
$ vagrant ssh -c 'sudo docker run -t -i ubuntu /bin/bash'
Unable to find image 'ubuntu' locally
Pulling repository ubuntu
d2099a5ba6c5: Download complete 
3db9c44f4520: Download complete 
5cf8fd909c6c: Download complete 
6006e6343fad: Download complete 
cc0067db4f11: Download complete 
7656cbf56a8c: Download complete 
511136ea3c5a: Download complete 
845a7ff0bf5a: Download complete 
a6c8f8708259: Download complete 
ac4bfb69e710: Download complete 
101e9f33c3dc: Download complete 
e41f31e92d60: Download complete 
6cfa4d1f33fb: Download complete 
086a54ed1641: Download complete 
35f6dd4dd141: Download complete 
9425702d2b8b: Download complete 
53e0ea871c5d: Download complete 
5e9838970f44: Download complete 
902710ffbd62: Download complete 
42ffda5fb276: Download complete 
c47d897f1a44: Download complete 
7baf0ef6f14a: Download complete 
e497c7c1bfbb: Download complete 
root@a914ff09a792:/# 
```


## Running tests

```sh
$ bundle
$ bundle exec rake spec
```
