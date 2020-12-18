# Trace-Labs-VM-Ras-Pi-Build

## Announcement
This repo is now being hosted and actively developed over on the Trace Labs page: https://github.com/tracelabs/Trace-Labs-VM-Ras-Pi-Build

### Introduction
This project ports the Trace Labs OSINT VM over to a Raspberry Pi and was made possible by the work done by Offensive Secuirty. The core of this repo revolves around the build scripts created by them: 
https://gitlab.com/kalilinux/build-scripts/kali-arm

The below process has only been tested on Debian flavors of Linux:
* Start by cloning this repo to a Debian based system and navigate in to the `Trace-Labs-VM-Ras-Pi-Build` directory
* Run `sudo build-deps.sh` - this will get your current system ready to build the Kali Pi image.
* Run `sudo rpi3-64-build.sh <image name>` - This script gives you the option to install tools or not. Choosing "y" will take longer but you will end up with a fully built out OSINT system at the end. Selecting "n" will just build a bare bones Kali Pi system.
* Burn the resulting `.img` file to an sd card as you normally would for a pi image.


### Explanation
`rpi3-64-build.sh` does several things:
* Lays the groundwork on the host system to build our Kali Pi image
* Uses `debootstrap` to lay down a basic Linux operating system and the tools needed to run it
* Writes a text file:`third-stage` to the Kali Pi system directory created in the above step. From here, the `third-stage` text file is executed and a bare bones Kali Pi system is installed. No tools are installed at this point but is instead the "kali-core" set of packages.
* If "y" was selected at the beginning then `install-packages.sh` will be ran. This is the text file containing instructions to install all the OSINT tools.



### Troubleshooting 
If the "rpi-64-build.sh" is throwing errors from the beginning, you may need to move the entire folder outside of your home directory before running.
