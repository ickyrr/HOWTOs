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

## Add all SDK packages including System Images (for better results)

- If you get this error during installation:

>ERROR : No emulator images (avds) found.
>1. Download desired System Image by running: /home/ickyrr/Android/Sdk/tools/android sdk
>2. Create an AVD by running: /home/ickyrr/Android/Sdk/tools/android avd
>HINT: For a faster emulator, use an Intel System Image and install the HAXM device driver

- Just follow the instructions and enter 
		/home/ickyrr/Android/Sdk/tools/android sdk
- and
		/home/ickyrr/Android/Sdk/tools/android avd
- The commands above will download all the necessary packages to run meteor on android emulator.

