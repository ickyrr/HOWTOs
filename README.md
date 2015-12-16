#INSTALLING ANDROID ON LINUX

##Using Ubuntu Make
-------------------------------

- If you're running Ubuntu, the easiest way to install both a Java Development Kit and Android Studio is by using Ubuntu Make, a command line tool that sets up various development environments and all dependencies for you.

- If you're on Ubuntu 14.04 LTS, you'll have to add the Ubuntu Make ppa first:

    sudo add-apt-repository ppa:ubuntu-desktop/ubuntu-make
    sudo apt-get update

- Then, you can install Ubuntu Make itself:

    sudo apt-get install ubuntu-make

- And finally you use Ubuntu Make to install Android Studio and all dependencies:

    umake android

