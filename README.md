# java-dev-on-ubuntu
Setting up a Java development environment on Ubuntu desktop.

Our current development environment is going to consist of:
1. Ubuntu 18.04 LTS
2. asdf version manager with Java extensions
3. Eclipse with git integration

## 1. Ubuntu 18.04 LTS
This guide is not going to cover the installation and configuration of the OS or the tools and utilities used to reach this point but they are confirmed here for completeness:
- [ ] Next clean installation change this section to include the details on how to check for and correctly install some of the utilities, especially cover ssh key file permissions.
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

We're going to install Java oracle-8.181:(While we still can!)
```
asdf install java oracle-8.181
```
The command initiates the download of the selected JDK which can take a while, but once complete the JDK should have been successfully installed.

We'll use this version system wide:
```
asdf global java oracle-8.181
```
But once setup properly you could use different versions per project by setting the asdf java on that directory.

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

If during some future tinkering you need to modify something about your locally installed versions of the JDK then you can find the install directories here:
```
/home/yourusername/.asdf/installs/java
```


## 3. Eclipse
We will install Eclipse Photon in this guide, download it from https://www.eclipse.org/downloads/

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
/home/yourusername/eclipse/jee-photon
```

Read and accept the licenses. When the installation completes, choose the launch option; the first action is to select a directory as a workspace, you can select any directory but of you want to follow this guide exactly then set it to:
```
/home/yourusername/Studio/Dev/eclipse-workspace
```
Once Eclipse has started you may dismiss the Welcome screen and uncheck the "Always show Welcome at start up" option, unless you like it and want to be welcomed every time, totally up to you.

## 4. Version control with Git and Eclipse Egit

This section covers a few large and complicated topics, we don't have the scope here to cover them in detail, but here are some links please take the time to read each one you are not familiar with.

### 4.1 Version control and Git
If you're here there's a good chance you know what version control is, if not just know it's a type of system used by developers to manage the source code they write. Obviously there is a lot more to it than that and the following link provides an excellent overview of how Git works and compares it to some of the other systems. [Git for Eclipse Users]http://wiki.eclipse.org/EGit/Git_For_Eclipse_Users

### 4.2 Installing EGit
Our version of Eclipse already as Egit installed. We will confirm this in the next section.

### 4.3 EGit User Guides
The guides listed in this section are extensive covering many aspects of EGit you may not use, but it might be good to know they exist.

> You may jump to the next section to continue with a simple
> step-by-step guide, but remember the guides listed here
> have much more information which you may find useful.

* [Official EGit User Guider] http://wiki.eclipse.org/EGit/User_Guide#Getting_Started.2FAdding_a_project_to_version_control
* [Vogella: Git version control with Eclipse/Egit] http://www.vogella.com/tutorials/EclipseGit/article.html#exercise-working-with-a-local-git-repository-in-eclipse

## 5. Step-by-step: Setting up your local Eclipse Git friendly Workspace
### Step 1: Where's git? Egit? ...anyone?
From the main Eclipse window navigate to  **Window** > **Show View** > **Other** this will open the **Show View** window.
![](images/screenshots/01-1-Menus.png?raw=true)

In the search bar enter *'Git'* if everything is installed correctly this will display a list of the available Git views. If the *'Git'* options are not displayed then you will need to perform some troubleshooting which is beyond the scope of the current guide; but as a hint make sure you've installed the correct version of Eclipse.
![](images/screenshots/02-Menus.png?raw=true)

While we're here let's add the **Git Repositories** view to our workspace by selecting it and choosing **Open**.

It might be added to the bottom part of your workspace like this:
![](images/screenshots/03-1-MoveWindow.png?raw=true)

I prefer to have it to the left, next to the **Project View** you can simply drag it by clicking in the *title bar* and moving it to your desired destination.
Like this:
![](images/screenshots/04-MoveWindow.png?raw=true)

### Step 2: Clone GitHub projects
There are many (...well a few) ways to clone these cats... umm sorry projects. We'll start with the simplest and work our way up.

**Using HTTPS**
In a web browser navigate to a GitHub project home of your choice, but definitely choose to go to this one if you're following the guide closely:
![test-github-clone](https://github.com/ockertbotha/test-github-clone)

On the page; make sure you're viewing the **<> Code** tab, click on the *'Clone or download'* button, if the box opens up a **Clone with SSH** title,
click the *'Use HTTPS'* link.
![](images/screenshots/05-1-GithubFirstCloneSSH.png?raw=true)

With the **Clone with HTTPS** details showing you can copy the URL by clicking the copy button.
![](images/screenshots/06-1-GithubFirstCloneHTTP.png?raw=true)

From the **Git Repositories** view we opened earlier click on the *'Clone a Git repository'* link this will open the *'Clone Git Repository'* window,
paste the URL we copied from *'GitHub'* into the URI field the rest of the underlined fields automatically populate after the paste,
but check that they match the values below. For this type of *'Clone'* we won't need any authentication and you may click *'Next'*.
![](images/screenshots/07-EgitSourceSetting.png?raw=true)

When the *'Branch Selection'* window launches it should have selected the *'master'* by default, if not then make sure it is selected, and click *'next'*.
![](images/screenshots/08-EgitBranchSelection.png?raw=true)


Since we're keeping things simple this time around, in the *'Local Destination'* window change the value of the *'Directory'* field to:
```
/home/yourusername/Studio/Dev/test-github-clone
```
and click *'Finish'*.
![](images/screenshots/09-EgitLocalDestination.png?raw=true)

Voila! The project is cloned.
![](images/screenshots/10-EgitCloneComplete.png?raw=true)

Let's use the Terminal to take a look at what was cloned, the first command navigates us to the correct starting place for the commmands
that follow, but as long as the path given to any of the commands resolves correctly you can do this anyway you like:
```
cd ~/Studio/Dev

tree test-github-clone/
```
![](images/screenshots/11-TreeOnTestProject.png?raw=true)

As you can see there is currently only the README.md file in the root of the project, this might change
as we test a few concepts but as long as you have the directory and some files you're good.

That view of the project is as much as we are really interested in, but of course there is a lot more to a git project
and if you interested to see the full scope of what we have cloned you can run the following command:
```
tree -lsa test-github-clone/
```
![](images/screenshots/12-FullTreeOnTestProject.png?raw=true)

## Workspace v Project Directory
> Before we go any further, if you've paid attention and particularly if you're
> familiar with Eclipse you will have noticed that we did not clone the
> Project into our Workspace, we will be importing the Project into
> our Workspace but to prevent git detecting and potentially including
> any Eclipse specific files we'll keep Eclipse away from the Project directory.

### Step 3: Managing a project in Eclipse Workspace
First we'll import the cloned project into our workspace. On the *'Git'* tab, select the cloned project, right-click to launch
the context-sensitive menu and select *'Import Projects'*
![](images/screenshots/13-EclipseImportProjectMenu.png?raw=true)

We're keeping things simple so, on the *'Import Projects...'* window that opens
make sure that the path of the *'Import Source'* field points to the root
of the cloned project and select *'Finish'*.
![](images/screenshots/14-EclipseImportProject.png?raw=true)

Once the import has completed the project including the README.md is available
to view in your *'Eclipse Workspace'*
![](images/screenshots/15-EclipseAfterProjectImport.png?raw=true)

Make changes: branch? / commit.

Delete project.

### Step 4: Add a local git project
You can clone git repo from anywhere and even keep them local, which doesn't seem like a good idea for anything that would be worth creating a repo for in the first place,
but just so that we can say "We Got The T-Shirt" here we go...

### Step 5: Getting SSH Access to a GitHub Repository
