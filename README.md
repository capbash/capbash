capbash
=======

A simple infrastructure tool that uses capistrano and bash to manage remote servers.

This project is meant to change very little, so if you want to check the activity, please refer to the
bootstrap project

https://github.com/aforward/capbash-bootstrap

# How to Install #

```
git clone https://github.com/aforward/capbash YOUR_REPO_ROOT
cd YOUR_REPO_ROOT
./bootstrap
```

This will clone the core capbash project, which you are supposed to edit a will.  It will
clone a submodule (https://github.com/aforward/capbash-bootstrap) which contains all the necessary
code to deploy to your servers, this way you can stay current on all development by simply
pull updates.

# How to Deploy #

Right now, you can't do much of anything, check for yourself.

```
cd YOUR_REPO_ROOT
./deploy
```
