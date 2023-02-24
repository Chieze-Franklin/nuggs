# Automating Machine Setup: Setting up Mac and Ubuntu Machines with Scripts in Makefiles

![image](https://user-images.githubusercontent.com/6097630/221061622-522f30e8-bc26-41e1-9fe1-19add2595d9a.png)

Setting up a new machine can be a time-consuming and error-prone task. Fortunately, you can automate the process using scripts and makefiles.
In this blog, we'll walk you through the process of setting up a Mac and Ubuntu machine using scripts in makefiles.

[Make](https://www.gnu.org/software/make/) is a build automation tool that is used to build and compile software projects.
Linux and Mac machines typically come with Make preinstalled and you can easily find and download it for your operating system online.
[Makefiles](https://www.gnu.org/software/make/manual/make.html#toc-An-Introduction-to-Makefiles) are configuration files that contain instructions
for `make` on how to build a project. By using makefiles, you can automate repetitive tasks, such as setting up a new machine.

The first step is to create a makefile that contains instructions for setting up your machine. Here's an example of what your makefile might look like:

```makefile
.PHONY: all setup-mac setup-ubuntu

all: setup-mac setup-ubuntu

setup-mac:
    ./setup-mac.sh

setup-ubuntu:
    ./setup-ubuntu.sh
```


This makefile has three targets: `all`, `setup-mac`, and `setup-ubuntu`. The `all` target is the default target that will be run when
you execute the make command. The `setup-mac` and `setup-ubuntu` targets call shell scripts (`setup-mac.sh` and `setup-ubuntu.sh`, respectively)
that contain instructions for setting up a Mac and Ubuntu machine, respectively.

To create the `setup-mac.sh` script, open a text editor and add the following instructions:

```bash
#!/bin/bash

# Install Homebrew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"

# Install software using Homebrew
brew install git
brew install node
```

These instructions will install Homebrew (a package manager for macOS) and then use Homebrew to install Git and Node.js.

To create the `setup-ubuntu.sh` script, open a text editor and add the following instructions:

```bash
#!/bin/bash

# Install software using apt-get
sudo apt-get update
sudo apt-get install -y git
sudo apt-get install -y nodejs
```

These instructions will update the Ubuntu package lists and then use apt-get to install Git and Node.js.

Once you have created your makefile and shell scripts, navigate to the directory containing your files in your terminal and run the `make` command.
This will execute the instructions in your makefile and set up your machine according to your specifications.

### My Personal Setup

Instead of calling external shell scripts, you can include your scripts in the Makefile itself. This is the setup I use. I have 2 distinct Makefiles:
1. [For Mac](https://github.com/Chieze-Franklin/makefiles/blob/master/machine_setup/mac/Makefile)
2. [And for Ubuntu](https://github.com/Chieze-Franklin/makefiles/blob/master/machine_setup/ubuntu/Makefile)

They install relevant software development tools on my machines. Feel free to download and run the appropriate one on your machine.

### Conclusion

Using scripts and makefiles is an efficient way to automate the process of setting up a new machine.
By writing a makefile with instructions for shell scripts, you can ensure that your machine is set up consistently and accurately every time.

### Learning Resources

- [Makefile Tutorial](https://makefiletutorial.com/)
- [Practice Makefiles Online](https://tio.run/#make)
- [Shell Scripting Tutorial](https://www.shellscript.sh/index.html)

-----

> This post was published from GitHub to Medium.
>
> The content of this post was scaffolded with the help of ChatGPT
