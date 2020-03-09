# Flashing Linux with Persistent Saving

If this is your first time creating a Linux drive, I'd recommend [using the tutorial version](https://github.com/CPHT/ILP/blob/master/LinuxPersistence/TutorialVersion.md/0.TableofContents.md)

## Table of Contents

:one:[Summary](#summary)<br>
:two:[Introduction](#introduction)<br>
:three:[Requirements](#requirements)<br>
:four:[Getting Started](#gettingstarted)<br>
:five:[First Terminal Commands](#firstterminalcommands)<br>
:six:[Adding Mkusb](#addingmkusb)<br>
:seven:[MKUSB](#mkusb)<br>
:eight:[Reboot and Test](#rebootandtest)<br>

<div id="summary"/>

## :one: Summary

This tutorial will help you flash the Ubuntu Linux operating system onto a USB flash. Unlike with just a live version, this guide will allow you to have both a live version of linux and a live version with persistent saving. After going through this tutorial, you will have a portable OS drive that you can get used to working with before committing to a full version. 

<div align="center">

---
<h3><b>:notebook_with_decorative_cover: Heads Up! :notebook_with_decorative_cover:</b></h3>


For doing this, you will need to have either a linux system already on hand or a usb with a live version.

<h3><b>:notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover:</b></h3>

---
</div>



<div id="introduction"/>

## :two: Introduction

Learning how to use Linux is critical for anyone interested in the tech industry. Linux is a free, open-source operating system that gives you freedom that neither macOS or Windows can achieve. Linux allows you to customize how you want the software to operate and not worry about clogging your OS with useless applications. In terms of security vulnerabilities Linux can be solved and caught sooner compared to Windows due to being open-source with countless users contributing to Linux improvements. 

Plus, Linux teaches you a more fun and graphically pleasing way on how the terminal works.

<div id="requirements"/>

## :three: Requirements

A couple of requirements you will need for this tutorial.

:radio_button: Linux already on a usb or an OS running the system: If running off a USB you'll need to change the boot loader sequence.<br>
:radio_button: A separate flash drive with at least 8 GB up to 64 GB: I recommend one that is USB 3.0 or better. This will also be needed if you want to install a full version.<br>
:radio_button: Linux .iso file: You can [click here](https://ubuntu.com/download/desktop) for the latest stable version. Currently, persistent-live versions of Ubuntu are able to be created with 18.04.3, 18.04.4, and 19.10<br>


<div align="center">

---
<h3><b>:notebook_with_decorative_cover: Heads Up! :notebook_with_decorative_cover:</b></h3>

For the persistence Linux drive, you can only use Debian or Ubuntu distributions at the current time of this guide being published. Hence why we are using Ubuntu as well as ubuntu being the most popular distro to learn. 

<h3><b>:notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover:</b></h3>

---
</div>

<div id="gettingstarted"/>

## :four: Getting Started

Before moving into Linux, there's a good chance you will have to change the secure boot loader. If you have already switched your boot loader and put the live usb device as top priority, you should go into a Linux live session user.  

:radio_button: Load into Linux.<br>
:radio_button: Get connected to the Internet.<br>
:radio_button: Open the terminal. You can either search for the application or use the keyboard shortcut `CTRL+ALT+T`.<br>

<div id="firstterminalcommands"/>

## :five: First Terminal Commands

For getting everything started, this may also be the first time you will be pulling down packages/dependencies from the command line. The visuals will broadcast just how cool it is working with the terminal. 

First you will need to enable the correct software repositories. Linux has four official software repositories: Main, Restricted, Universe, and Multiverse. We are concerned with getting universe.

:radio_button: On your terminal, type the following command:<br>

`sudo add-apt-repository universe`


<div align="center">

---
<h3><b>:notebook_with_decorative_cover: Heads Up! :notebook_with_decorative_cover:</b></h3>

To make it easier when you type in the terminal, hitting TAB will fill in some of the commands for you when typing. 

<h3><b>:notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover:</b></h3>

---
</div>

<br><br>

In case this is your first time working with Linux from the terminal, I've provided some short descirptions on the commands being issued throughout the tutorial.

| Command | Meaning | Description |
|---|---|---|
|sudo| super user do| Tells the computer that I am the administrator/ powerful user. Will always require a login if it is a user account.|
|add| add package| Tells the computer to add the following package|
|apt| advanced packaging tool| quick advanced way to interact with <b>.dpkg</b> for Debian sections.|
|repository| repository | grabs the repository name of your package.|

<br>What this is telling the computer is "Hey! I am the super user! I want you to add an advance packaging tool. This advance packaging tool (apt) is from a repository called universe." 


<div align="center">

---
<h3><b>:notebook_with_decorative_cover: Heads Up! :notebook_with_decorative_cover:</b></h3>

<b>Note</b>: depending on the live USB, you may get the following message below:

<h3><b>:notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover:</b></h3>

---
</div> 

<br><br><kbd><img src="/LinuxPersistence/img/LinuxPersistence01.png"><br><i>Figure 5.1: Linux terminal for adding repository.</i></kbd><br><br>

If you get the message above when adding the repository, your Linux already has `universe` enabled. 

Now you need to run an update for your computer. This will grab any dependencies or new versions that require an update.

:radio_button: Still on your terminal, type in the following command:<br>

`sudo apt-get update`

This will tell the terminal to get any updates regarding our packages already installed. 

<br><br><kbd><img src="/LinuxPersistence/img/LinuxPersistence02.png"><br><i>Figure 5.2: Linux terminal updating packages.</i></kbd><br><br>

<div id="addingmkusb"/>

## :six: Adding Mkusb

Mkusb is the application we will work with which can install Linux with a persistent save option. When we add this on, think of it like Linux live but with bonus content. Before installing a full version, you get a chance to see apps added on and still work with them. This will be the first program you can pull down from the command line.

:radio_button: Back on your terminal, type in the following:<br>

`sudo add-apt-repository ppa:mkusb/ppa`

`PPA` is short for personal package archive. The PPA's that you download come from the platform called Launchpad. Launchpad is used for developers who create their own software and can be downloaded by others through their own repositories. 

:radio_button: You'll get a message that pops up to learn more information. Hit enter to continue.<br>
:radio_button: Wait for everything to build again.<br>

<br><br><kbd><img src="/LinuxPersistence/img/LinuxPersistence03.png"><br><i>Figure 6.1: Linux terminal for adding repository mkusb.</i></kbd><br><br>

:radio_button: Update the packages on your system again with the following: `sudo apt-get update`<br>

Now that we have added the PPA repository, we now need to add and install the actual package.

:radio_button: On the terminal, type in the following:<br>

`sudo apt install --install-recommends mkusb mkusb-nox usb-pack-efi`

<br><br><kbd><img src=/LinuxPersistence/img/LinuxInstallingAll3packages.png><br><i>Figure 6.2: Linux terminal installing multiple packages.</i></kbd><br><br>

Couple of things to remember with the new commands
<br><br>

|command|explanation|
|----|------|
|install| tells the terminal to install the following packages
|--install-recommends| installs the recommended packages for the following application. 

<br>The three packages `mkusb`, `mkusb-nox`, `usb-pack-efi` are what we will need to help create a safe, bootable, persistent Linux distro.

:radio_button:<b>mkusb</b>: The graphical version of mkusb. You'll be using this for the first time.<br>
:radio_button:<b>mkusb-nox</b>: This is the command line version for using mkusb.<br>
:radio_button:<b>usb-pack-efi</b>: This package is needed for being able to create persistence saving with UEFI and BIOS.<br>

Now go ahead and update your system. Type in the following command again.

:radio_button:`sudo apt-get update`<br>
:radio_button: Stay on your terminal for the next section.<br>

<div id="mkusb"/>

## :seven: MKUSB

Now that everything is accounted for, we can move forward with flashing the persistent Linux distro on the flash drive of your choice. Now you can do this from the command line as well but for now I will show you with the graphical interface to get you started.

Before we start, go ahead and plug in the USB you want to flash Linux to. The usb should already be mounted when it's plugged in. However, you need to know where the USB is mounted at. You can check this real quick.

:radio_button: Plug in the usb you will write Linux to.<br>
:radio_button: Open up a new terminal (CTRL+ALT+T).<br>
:radio_button: Type if the following command: `df`.<br>

The command `df` displays the filesystems that are currently mounted for your computer as well the path they are located at. 

:radio_button: Find the filesystem that your usb is mounted on. In this tutorial, I'm looking for <b>USBRED</b>. Your name for the USB drive may be different.

<br><br><kbd><img src="/LinuxPersistence/img/LinuxUSBLocation.png">
<br><i>Figure 7.1: All filesystem locations currently mounted.</i></kbd><br><br>

:radio_button: Either memorize what filesystem the USB is mounted on or minimize the terminal for it. You'll need it when selecting the correct file path.<br>
:radio_button: Go back to the previous terminal you were using.<br>
:radio_button: Type in the following command on the terminal: `mkusb`<br>

You should be presented with the following screen:<br>

<br><br><kbd><img src="/LinuxPersistence/img/Linuxmkusbcommand.png"><br><i>Figure 7.2: Mkusb version selection.</i></kbd><br><br>

:radio_button: Type `d` as your selection. This will give the newest interface that mkusb created.<br>
:radio_button: You'll get a `Do USB Stuff` screen that pops up warning you the device you will select will be overwritten completely when flashing the Linux iso. Click Ok.<br>

<br><br><kbd><img src="/LinuxPersistence/img/LinuxDoStuffDUS.png"><br><i>Figure 7.3: Overwriting warning.</i></kbd><br><br>

:radio_button: Select of type `i` for installing a live usb.<br>

<br><br><kbd><img src="/LinuxPersistence/img/Linuxinstallmakeabootdevice.png"><br><i>Figure 7.4: General command you want to do.</i></kbd><br><br>

:radio_button: Select p or `persistent-live` for debian and ubuntu iso.<br>

<br><br><kbd><img src="/LinuxPersistence/img/LinuxPersistentLiveChoice.png"><br><i>Figure 7.5: Persistent live selection.</i></kbd><br><br>


<div align="center">

---

<h3><b>:notebook_with_decorative_cover: Heads Up! :notebook_with_decorative_cover:</b></h3>

After this step you may have a screen pop up saying a quick boot choice. 

<br><br><kbd><img src="/LinuxPersistence/img/LinuxQuickBoot.png"><br><i>Figure 7.5.1: Quick install option.</i></kbd><br><br>

This may happen if you have plugged in your new USB already. If not, it shouldn't pop up or may be asking you to overwrite your main drive (Which may be Windows in this case). Click the X in the top right corner to close the window. 

<h3><b>:notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover:</b></h3>

---
</div>

:radio_button: Find the file location for the linux iso you want to burn.<br>

<br><br><kbd><img src="/LinuxPersistence/img/LinusISOlocation.png"><br><i>Figure 7.6: Ubuntu iso location.</i></kbd><br><br>


:radio_button: On the `Select target device` screen, choose the usb where it is mounted. This is what I mean for knowing where the USB you want to flash is located at.<br>

<br><br><kbd><img src="/LinuxPersistence/img/LinuxTargetDriveDevice.png"><br><i>Figure 7.7: Target device you want to write to.</i></kbd><br><br>


<div align="center">

---

<h3><b>:bangbang: Warning :bangbang:</b></h3>
:interrobang::interrobang::interrobang:

Be very careful as to not accidentally overwrite your main drive. That will be indicated by the <b>built in device</b> under the <b>kind of device</b> setting.

:interrobang::interrobang::interrobang:

</div>

---


:radio_button: For the live drive settings, select the `upefi`. Upefi uses the grub system off the ISO file and works with multiple computer manufacturers.<br>

<br><br><kbd><img src="/LinuxPersistence/img/Linuxdrivesettings.png"><br><i>Figure 7.8: Persistent drive settings.</i></kbd><br><br>

:radio_button: Assign how much persistence you want to give your USB stick. The default is 50, which means the other 50 percent of your usb drive will be used for storage.<br>

<br><br><kbd><img src="/LinuxPersistence/img/Linuxpersistenceallowed.png"><br><i>Figure 7.9: Persistent percentage slider.</i></kbd><br><br>

:radio_button: Select Go on the final checkpoint screen.<br>
:radio_button: Wait for the process to finish. either keep an eye on the terminal or the gui if you have it pulled up.<br>

<br><br><kbd><img src="/LinuxPersistence/img/Linuxmkusbprogress.png"><br><i>Figure 7.10: Persistent progression. </i></kbd><br><br>

:radio_button: Exit out of the remaining windows that pop up for mkusb.<br>
:radio_button: If not already unmounted, unmount the usb you just flashed the persistence saving usb to.<br>
:radio_button: Remove the device from the usb drive.<br>

<div id='rebootandtest'/>

## :eight: Reboot and Test


Now you will get the chance to test out the persistence live version of Linux! Hopefully, you will enjoy using the device so much you may want to install the full version. We will also make some minor changes on your account, verifying that you do have a persistence saved Linux OS.

:radio_button: Shutdown your pc and reboot with the newly created flash drive.<br>


<div align="center">

---
<h3><b>:notebook_with_decorative_cover: Heads Up! :notebook_with_decorative_cover:</b></h3>

You boot options should still be the same if you were previously on a Linux live version.

<h3><b>:notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover:</b></h3>

---
</div>

 

You will have a new menu that appears called the GRUB. This is the interface you would normally see that takes precedent to choose which OS you would like to run.

<br><br><kbd><img src="/LinuxPersistence/img/LinuxGrubmenu.PNG"><br><i>Figure 8.1: Linux boot options. </i></kbd><br><br>

:radio_button: Choose the first option <b>persistent live</b><br>
:radio_button: Wait for ubuntu to load.<br>


<div align="center">

---
<h3><b>:notebook_with_decorative_cover: Heads Up! :notebook_with_decorative_cover:</b></h3>

Ubuntu will take a bit to load when booting vs a full install. You may also have a black screen showing information regarding APCI failure. It will bypass this and continue to boot into ubuntu.

<h3><b>:notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover: :notebook_with_decorative_cover:</b></h3>

---
</div>


After the loading process is complete, you will be presented with the interface that a live version of ubuntu looks like when first approaching. The taskbar will be on the left and have the preloaded applications available. It will also have the default background that you would see on a live version.  The difference you will see is there will be two partitions on the desktop screen: `usbdata` and `casper-rw`.

<br><br><kbd><img src="/LinuxPersistence/img/Screenshot%20from%202020-01-31%2007-04-04.png"><br><i>Figure 8.2: Linux on persistent bootup.</i></kbd><br><br>

Anything saved into the `usbdata` partition can be accessed on Windows and MacOs. Any persistence or operations saved for linux move to the `casper-rw`. An easy change to see if your preferences are saved is moving the task bar somewhere else. After making your changes, shut down the computer and boot back up into persistent mode. See your results on next bootup.

<div align="center">

---

<h3><b>:bangbang: Warning :bangbang:</b></h3>
:interrobang::interrobang::interrobang:

If by chance your system is taking a long time to boot up, you may have to switch to the live version, which you can save files and applications to the `usbdata` partition, but operation changes will not be saved. Slow boot time can be caused by a multitude of problems. You can [view some simple solutions](https://github.com/CPHT/ILP/blob/master/LinuxPersistence/PersistenceTrouble.md) for more information if you are having trouble. 

:interrobang::interrobang::interrobang:

</div>

---


