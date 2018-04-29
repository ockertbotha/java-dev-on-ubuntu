# java-dev-on-ubuntu
Setting up a Java development environment on Ubuntu desktop.

Our current development environment is going consist of:
1. Ubuntu 16.04 LTS
2. asdf version manager with Java extensions
3. Eclipse with git integration

## Ubuntu 16.04 LTS
This guide is not going to cover the installation and configuration of the OS, tools or utilities used to reach this point but they are confirmed with versions where appropriate for completeness:
- Ubuntu 16.04 LTS
- git-core
- curl
- ssh
- atom.io (https://atom.io/) for text editing needs

## asdf
This will enable us to not only install our JDKs but also switch between them on a per project basis, the core of the utility following the instructions here: https://github.com/asdf-vm/asdf

Once asdf is installed and configured, add the Java plugin with:
```
asdf plugin-add java
```

Check for the available versions with:
```
asdf list java
```

Were going to install Java 8.172 and use it system wide:
```
asdf install java 8.172
asdf global java 8.172
```

Check for the current version with:
```
asdf current java
```
