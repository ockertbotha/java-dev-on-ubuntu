# java-dev-on-ubuntu
Setting up a Java development environment on Ubuntu desktop.

Our current development environment is going consist of:
1. Ubuntu 18.04 LTS
2. asdf version manager with Java extensions
3. Eclipse with git integration

## 1. Ubuntu 18.04 LTS
This guide is not going to cover the installation and configuration of the OS or the tools and utilities used to reach this point but they are confirmed here for completeness:
- Ubuntu 18.04 LTS
- git-core
- curl
- ssh
- atom.io (https://atom.io/) for text editing needs

Unless it is stated differently, all commands should be entered using the Terminal.

## 2. asdf
This will enable us to not only install our JDKs but also switch between them on a per project basis, install the core of the utility following the instructions here: https://github.com/asdf-vm/asdf

Close the Terminal and start a new one so that the changes
can take effect.

Once asdf is installed and configured, add the Java plugin with:
```
asdf plugin-add java
```

Check for the available versions with:
```
asdf list-all  java
```

We're going to install Java 8.172:
```
asdf install java 8.172
```

We'll use this version system wide:
```
asdf global java 8.172
```

Check for the current version with:
```
asdf current java
```

Since we applied our version globally running the following anywhere should confirm the asdf settings:
```
java -version
```

If all is not as it seems you can confirm which java is running with:
```
which java
```
Which should point to your version of the shims file:
```
/home/yourusername/.asdf/shims/java
```
Intrepid readers can learn more about shims here (https://en.wikipedia.org/wiki/Shim_(computing))


## Eclipse
We will install Eclipse Oxygen in this guide, download it from https://www.eclipse.org/downloads/

Extract:
```
tar xfz ~/Downloads/eclipse-inst-linux64.tar.gz
```

Install:
```
~/Downloads/eclipse-installer/eclipse-inst
```
