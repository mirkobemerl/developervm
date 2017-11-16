# Introduction
The target of this project is to provide a development environments. It is insecure and not for production environments.
This README gives an overview, more information are in the [wiki](http://wiki.system.local/display/OTA/DeveloperVM).

Some highlights:
* The system wide proxy is set
* Tool specific proxy is set, e.g. the javakeystore or the proxy in docker to pull images
* An X-System is installed with a two monitor setup

# Setup
## Process
* Install [vagrant](https://www.vagrantup.com/downloads.html) (1.9.3) and [virtualbox](https://www.virtualbox.org/wiki/Downloads) (5.1.26)
* Clone Vagrantfile via `git clone ssh://git@git.system.local:7999/aems/developervm.git` and store it on C:\developervm;
* Open Powershell (Windows-Key -> Powershell (x86))
* Change directory into it C:\developervm with `cd C:\developervm`
* Execute .\setup.ps1 and enter your u-number and former proxy (proxy is right now deprecated)
* Start the VM via virtualbox

In case you would like to start the vm in fullscreen, create a file:
Right click on desktop in windows -> new -> link (Verknüpfung) -> Change the target to `"C:\Program Files\Oracle\VirtualBox\VirtualBox.exe" --startvm DevelopmentBox --fullscreen`. Click next -> name it "DevelopmentBox" -> Click Finish. While system boot (while you see the black screen with just text), click on "Anzeige" -> "Virtueller Monitor 2" -> "Benutzer Host-Monitor 2"

## Login
You can login with the provided user number you entered while execute setup.ps1. The password is the 'start1'. Please change the password via `passwd` in the terminal.

# Provisioning
The user vagrant got a random password and the vagrant ssh-folder has been moved to /home/vagrant/ssh-safe. Please enable the ssh-keys by using the command `mv /home/vagrant/ssh-safe /home/vagrant/.ssh` in the VM.
Afterwards use the command "vagrant provision" to run the bootstrap again.

# Tools
## Visual Studio Code and Eclipse
Start it with the command `code --disable-gpu` to ensure it is displayed correctly. Eclipse can be started with `/opt/eclipse/eclipse`

## Docker
You can use docker with the vagrant user.
For example `docker run hello-world`

## Browser
* Firefox can be started with the normal `firefox` command
* Chromium can only be started with `$HOME/chromium.sh`

## Package Manager
The default package manager on the console is dnf. [Yum Extender (dnf)](http://www.yumex.dk/) offers a GUI, open via ´yumex-dnf´.

# Known Issues
See [Wiki-Page](http://wiki.system.local/display/OTA/DeveloperVM).

# Bug Reporting
Please report bugs with:
* Vagrant version (command `vagrant version`)
* Virtualbox version (Hilfe -> Über Virtualbox)
* Screenshot of the error/complete window
* Description of how the error occurred or a provide a screen-cast
