capbash
=======

A simple infrastructure tool that uses capistrano and bash to manage remote servers.

This project is meant to change very little, and delegates most of its work to a bootstrap project, shown below:
https://github.com/aforward/capbash-bootstrap

This allows you to clone the project, make it your own and still stay up on the current version.

# How to Install #

You will need to download the installer and run it.  This can be down with curl, as follows:

```bash
curl -s https://raw.githubusercontent.com/aforward/capbash/master/capbash-installer | bash
```

This will install capbash into /usr/local/bin/bash.  To install it somewhere else, for example:

```bash
curl -s https://raw.githubusercontent.com/aforward/capbash/master/capbash-installer | bash -s -- --path ~/.bin
```


# Server Preconditions #

Please ensure your new server has a root password, and that an ssh server / client is installed.  For example,

This will allow you give your root user a password:

```
sudo su root
passwd
```

And, this will install an ssh server / client on Ubuntu.

```
apt-get install openssh-server openssh-client
```

Capbash works as root, so you will need to enable root login.
```
vi /etc/ssh/sshd_config

# Change PermitRootLogin to be
PermitRootLogin yes
```


# Creating a New Capbash Project #

You can now create a new 'devops' project, by simply calling:

```bash
# default project name is devops
capbash new

# Or, name it what you want
capbash new deploys
```

This will create a new git project ready for remove deployment.


# Deploy to Remote Server #

To push the helloworld script to your server, all you need if the IP or hostname of your server (e.g. 192.167.0.48) and your root password.

```bash
capbash deploy <IP>
```

For example,

```bash
capbash deploy 127.0.0.1
```

# Adding Submodules #

Install scripts are written in bash, and can be added to your project. First you will want to list our available submodules.

```bash
capbash ls
```

Now, you can install any submodule, e.g. docker

```bash
capbash install docker
```

We are working on more submodules, as well as a registry to support third party modules.

# How to update capbash and all submodules #

This is pull all submodules, including capbash itself.

```bash
capbash update
```
