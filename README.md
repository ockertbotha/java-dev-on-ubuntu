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


## 3. Eclipse
We will install Eclipse Oxygen in this guide, download it from https://www.eclipse.org/downloads/

From your Downloads directory:
```
cd ~/Downloads
```

Extract:
```
tar xfz ~/Downloads/eclipse-inst-linux64.tar.gz
```

Launch the GUI installer with:
```
~/Downloads/eclipse-installer/eclipse-inst
```

You can select whichever version you wish but if you want to follow this guide then choose:
```
Eclipse IDE for Java EE Developers
```

Accept the default installation folder which should be your version of:
```
/home/yourusername/eclipse/jee-oxygen
```

Read and accept the licenses. When the installation completes, choose the launch option; the first action is to select a directory as a workspace, you can select any directory but of you want to follow this guide exactly then set it to:
```
/home/yourusername/Studio
```

## 4. Version control with Git and Eclipse Egit

This section covers a few large and complicated topics, we don't have the scope here to cover them in detail, but here are some links please take the time to read each one you are not familiar with.

### 4.1 Version control and Git
If you're here there's a good chance you know what version control is, if not just know it's a type of system used by developers to manage the source code they write. Obviously there is a lot more to it than that and the following link provides an excellent overview of how Git works and compares it to some of the other systems. [Git for Eclipse Users]http://wiki.eclipse.org/EGit/Git_For_Eclipse_Users

### 4.2 Installing EGit

### 4.3 EGit User Guides
The guides listed in this section are extensive covering many aspects of EGit you may not use, but it might be good to know they exist.

> You may jump to the next section to continue with a simple
> step-by-step guide, but remember the guides listed here
> have much more information you may find useful.

* [Official EGit User Guider] http://wiki.eclipse.org/EGit/User_Guide#Getting_Started.2FAdding_a_project_to_version_control
* [Vogella: Git version control with Eclipse/Egit] http://www.vogella.com/tutorials/EclipseGit/article.html#exercise-working-with-a-local-git-repository-in-eclipse

## 5. Step-by-step: Setting up your local Eclipse Git friendly Workspace
