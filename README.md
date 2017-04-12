<center><img src="https://s8.hostingkartinok.com/uploads/images/2017/03/b7c601dacee73c8f46cb95899ec9301b.png" height="100%" width="100%;"/></center>

##  Lets build Vanilla ##

We can now do this two different ways
 
### Option A  ###
Run the following commands to sync the InitalSetup script and then run it:

if you enter your correct distro as the first argument it will install all required packages from akhilnarang's scripts

currently supported distros: Ubuntu 16.04+ (enter "ubuntu"), Mint 18+ (enter "mint"),  Deepin (enter "deepin"), Arch (enter "arch"), and Manjaro (enter manjaro).

you can also enter "none" if you already have the packages set up

This script will also create the Vanilla directory for you.
```bash
git clone -b rinit https://github.com/VanillaNexusSource/vanilla_scripts rinit
bash rinit/InitalSetup.sh <distro> current
```
After InititalSetup finishes you should have the repo synced

Remove the rinit folder:
```bash
rm -rf rinit
```

### Option B ###

First off we should setup our enviroment if we haven't already. The easiest way to do it is by running the following commands (Note this is the scripts for ubuntu 16.04+, linux mint and deepin)
```bash
sudo apt-get install git-core
git clone https://github.com/akhilnarang/scripts
cd scripts
bash ubuntu1604linuxmint18.sh
cd ~
```
Lets make a directory for Vanilla and then open it:
```bash
mk dir Vanilla && cd Vanilla
```
Run the following commands:
```bash
repo init -u http://github.com/VanillaNexusSource/android_manifest.git -b 7.1.2 --no-clone-bundle
repo sync --force-sync -c --no-clone-bundle --no-tags --optimized-fetch --prune
```
We can now begin building Vanilla.

Before we continue we recommend enabling ccache THIS IS HIGHLY OPTIONAL

Run these commands:
```bash
ccache -m 50g
cd ~
nano .bashrc
```

When .bashrc opens in nano add export USE_CCACHE=true right under esac after a tab.

this should look like:
```bash
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
case $- in
    *i*) ;;
      *) return;;
esac

export USE_CCACHE=true
```
This also has two options

### Option A ###
Run this command to begin building Vanilla:
```bash
bash scripts/vanilla.sh <ram> <sync/nosync> <clean/noclean> <device> <pixel/nopixel>
```
An example of this would look like:
```bash
bash scripts/vanilla.sh sync noclean angler pixel
```
After the build is finished you can find your files in ~/Vanilla-Out catagorized in indivdual folders by date

### Option B ###
Run these commands to build Vanilla:
```bash
export PIXEL=true (if you dont want a pixel build don't worry about this)
. build/envsetup.sh
mka clobber
lunch vanilla_DEVICE_userdebug
mka vanilla
```
After it finishes you can find your files in /out/target/DEVICE The two files you need are going to be named vanilla_DEVICE-VERSION-git-built(-pixel)

### CONGRATS You have now built Vanilla ###