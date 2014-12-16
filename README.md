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

If you are cloning an existing repository, then you need to initialize the git submodules (if any):

```bash
# initialize git submodules
cd /path/to/capbash_project
capbash init

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

# How to update capbash #

To get the latest capbash capabilities, run

```bash
capbash update-self
```

# How to project specific modules #

From within your project, you can update all modules.

```bash
capbash update
```

Usage
=====

```bash
Usage

  capbash [action]

Global Actions (applies outside of any particular project)

  update-self             - Updates capbash to the lastest version
  ls                      - Show all available modules (e.g. docker, nginx)
  help                    - Displays this output.

Project Actions (applies to a specific project, and must be run from within that project)

  udpate                  - Updates all project modules, including the capbash bootstrap
  install <module>        - Installs a particular module into your project, e.g. 'capbash install docker'
  uninstall <module>      - Uninstalls the module, e.b. 'capbash uninstall nginx'

Deployment Actions (applies to a specific project, and is geared towards running things on remote servers)

  deploy <server> <node>  - Deploys to server (e.g. 192.169.10.11) and node (install scripts located in ./nodes directory)
  sync <server>           - Synchronizes project on remote server, but does not install / configure the node

```

Available Modules
=====

 * monit (for monitoring your server)
 * deploykeys (a simple public/private key manager to enable access to other servers / services)
 * git
 * docker (docker up and running in a jiffy)
 * elixir (installs a tagged version of elixir)

 * mysql (installs mysql in a docker container)

 * drupal (installs a drupal admin console for deploying one or more instances of drupal)
 * phoenix (installs phoenix web applications based on the elixir language)
 * nginx (a webserver running mostly within a container)
 * apache (a webserver running apache2)

