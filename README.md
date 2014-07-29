capbash
=======

A simple infrastructure tool that uses capistrano and bash to manage remote servers.

This project is meant to change very little, and delegates most of its work to a bootstrap project, shown below:
https://github.com/aforward/capbash-bootstrap

This allows you to clone the project, make it your own and still stay up on the current version.

# How to Install #

You will want to clone the project, and then bootstrap it.

```
git clone https://github.com/aforward/capbash YOUR_REPO_ROOT
cd YOUR_REPO_ROOT
./bootstrap
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

CHEF works as root, so you will need to enable root login.
```
vi /etc/ssh/sshd_config

# Change PermitRootLogin to be
PermitRootLogin yes
```


# Deploy to Remote Server #

To push the helloworld script to your server, all you need if the IP or hostname of your server (e.g. 192.167.0.48) and your root password.

```
./capbash deploy <IP>
```

For example,

```
./capbash deploy 127.0.0.1
```

# Adding Submodules #

Install scripts are written in bash, and can be added to your project. First you will want to list our available submodules.

```
./capbash ls
```

Now, you can install any submodule, e.g. docker

```
./capbash install docker
```

We are working on more submodules, as well as a registry to support third party modules.

# How to update capbash and all submodules #

This is pull all submodules, including capbash itself.

```
./capbash update
```
