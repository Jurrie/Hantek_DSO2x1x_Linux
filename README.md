# Hantek_DSO2x1x_Linux
![myimage-alt-tag](https://github.com/AndrewBCN/Hantek_DSO2x1x_Linux/blob/main/Pictures/hanteklinuxinside1a_small.jpg?raw=true)
## Linux for the Hantek DSO2000 series using Buildroot

This project provides the files and documentation to build and run from RAM a small Linux distribution for the Hantek DSO2000 series (DSO2C10, DSO2C15, DSO2D10, DSO2D15) "value" DSOs.
These inexpensive DSOs are powered by an AllWinner F1C200s SOC with 64MB of RAM, and Buildroot can be configured to build u-boot, the Linux kernel, the DTB file and a small root filesystem.
The files output by Buildroot can then be uploaded directly to the DSO RAM using sunxi-fel/USB, and then Linux can be started which will provide a serial terminal connection and USB mass storage emulation through the USB OTG connector on the back of the DSO.

In other words: there is absolutely no need to open the scope and this process does not void the warranty, since the NAND flash inside the DSO remains untouched.

This project borrows many ideas and some code from three distinct GitHuB repositories and Buildroot projects for the same F1C200s SOC:

1. Businesscard Linux by George Hilliard https://github.com/thirtythreeforty/businesscard-linux

2. Embedded Linux for the Lichee Pi Nano by Nick Matantsev https://github.com/unframework/licheepi-nano-buildroot

3. builroot-tiny200 by AODZIP https://github.com/aodzip/buildroot-tiny200

This project is a result of a thread on EEVBlog forum about hacking these Hantek DSOs:

https://www.eevblog.com/forum/testgear/hacking-the-dso2x1x/

## Pre-built files

The Pre-Built folder contains the files required to boot Linux on a DSO2x1x, so the instructions for building below can be skipped.

## Building

We use Buildroot (www.buildroot.org) to build all the required packages to boot Linux on the Hantek DSO2x1x. The building process takes a couple of hours or more depending on the speed of your machine and Internet connection.

1. Git clone this project and cd into the directory just created.
2. Download Buildroot and extract it into this project directory. The recommended version is the one we tested: buildroot-2021.05. This will create a directory /buildroot and you should cd into it.
3. Copy the files from this project into the corresponding folders in the buildroot directory: cp ../board ...
4. Prepare the buildroot configuration file: make hantek_dso2k_defconfig
5. [optional] At this point you can if you want edit the default Buildroot configuration file and save your own version. Check the Buildroot manual for instructions.
6. Start the build: make. You can make yourself a tea and/or watch a movie, because this takes a couple of hours or more.

## Loading Linux using sunxi-fel/USB

### From a PC running Windows

### From a PC running Linux

## Opening a root shell and transferring files to/from the DSO2x1x

## Developers

If you want to change the u-boot or Linux kernel version, or help development for this project, or simply "do it your own way" you can examine the default buildroot configuration file and modify it as explained above. Same applies to other configuration files, as well as all the other files in this project: once you think you have found/solved a bug or added a feature that you would like included here, just open an issue or a pull request.

## Contributors

Main contributor: AndrewBCN.
DSO2x1x master hacker and tester: DavidAlfa.
DSO2x1x and Lichee Pi Nano tester: aika.
