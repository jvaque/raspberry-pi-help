# Raspberry Pi Complete Settup

This is a file containing all the steps I follow when setting up my raspberry pi to ensure that I don't forget doing anything and avoid me from searching for the nth time on google and forums how to do basic stuff.

## Download the image etcher on your computer

Title is pretty self explanatory, go to the raspberrypi website > downloads and install the image etcher. Your typical windows program install, download, click, click, click, done.

## Etch the image you want to the microSD card

If you previously had an image written in the microSD card open the disk partition manager and delete both volumes and re-format them into a single volume. 

Run the etching program, select the latest version of Raspberry Pi OS Lite, select the microSD card (make sure you select the microSD card and not another device since whatever you select will be wiped) and wait for the program to finish.

Once finished unplug and plug back in the microSD card from the computer.

Finally create an empty file in the **boot** partition named **ssh** without any extensions so on first boot ssh will be enabled, since by default this is disabled for security reasons, and you can access your raspberry pi via ssh without having to plug in a mouse and monitor, if you don't intend to connect via ssh straight away (using it with a keyboard and monitor plugged in) skip this step.

## First boot

- Plug in the microSD card into your pi
- Plug in an ethernet cable to your pi
- Plug in power to your pi

This will start the fist boot this might take a couple of minutes so just wait and on the meantime log in to your LAN router and assign a static IP for your raspberry pi and take note of it.

After a couple of minutes the first boot settup should have been completed and now you can log in to your pi 🎉🎉🎉.

## SSH into your pi

Open a powershell terminal instance in your computer and type the following to ssh to your pi, substitute '192.168.1.XXX' with the static IP you assigned from your router

```console
PS C:\Users\username> ssh pi@192.168.1.XXX
```

The default raspbian password is **raspberry**

## Change password

Imediately change the password to a secure and unique password and write it down on your password manager as it's impossible to remember strong and unique passwords. To do this run the following.

```console
pi@raspberry $ passwd
```

After running the command you will be asked for a new password and after re-typing it it will be changed.

## Create new users -- not really necessary

(todo haven't really used any other user than pi)

## Update your raspberry pi

run the following commands in order to update all packages to the latest version

```console
pi@raspberry $ sudo apt update
pi@raspberry $ sudo apt full-upgrade
pi@raspberry $ sudo reboot
```

## Expand volume -- not sure if it is no longuer needed as sudo apt full-upgrade might already do it

// might not be needed as full-upgrade does this already
lsblk
expand volume
sudo raspi-config
lsblk

## Access your PI from outside your local nework using no-ip

follow this tutorials, still need to write the summary for this file
http://www.noip.com/support/knowledgebase/installing-the-linux-dynamic-update-client/?utm_campaign=getting-started&utm_medium=notice&utm_source=email
or 
https://www.noip.com/support/knowledgebase/install-ip-duc-onto-raspberry-pi/

mkdir /home/pi/noip
cd /home/pi/noip
wget https://www.noip.com/client/linux/noip-duc-linux.tar.gz
tar vzxf noip-duc-linux.tar.gz
cd noip-2.1.9-1
sudo make
sudo make install
sudo /usr/local/bin/noip2

// check connection
sudo noip2 ­-S

no-ip set up to start on system startup
configure router to enable ssh

## Install git
Unless you want to develop all of your code through the shell or ftp into your pi you will need git in order to pull from your remote repositories the code that you write in a modern text editor such as visual studio code.
follow tutorial https://linuxize.com/post/how-to-install-git-on-raspberry-pi/ to write the readme thing
get git
sudo apt install git // to install git on the pi

## Install pip
Because for some reason it doesn't come standard, not sure why, and set up virtual environments because they are amazing!!
//install pip (not really needed for venv as venv comes with python3)
sudo apt install python3-pip
get python venv virtual environment

## Get neofetch because it's cool 
wget https://github.com/dylanaraps/neofetch/archive/7.1.0.zip
unzip 7.1.0.zip
rm 7.1.0.zip

cd neofetch-7.1.0
sudo make install

neofetch
neofetch options
follow tutorial https://www.cyberciti.biz/howto/neofetch-awesome-system-info-bash-script-for-linux-unix-macos/
neofetch when you ssh into raspberry pi


## Install pi-hole because its amazing
pihole - https://pi-hole.net/
https://github.com/pi-hole/pi-hole/#one-step-automated-install
curl -sSL https://install.pi-hole.net | bash