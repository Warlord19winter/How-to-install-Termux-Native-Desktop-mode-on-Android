# How-to-install-Termux-Native-Desktop-mode-on-Android

The Best Way to use Termux

No Proot/ No Chroot/ No Ai/ No Scripts

Straight Native Termux Desktop Mode

----------------------------------------------------------------------------------------------------------------------

The Pros and Cons

Native: Runs directly inside Termux. Faster, lighter, better performance.

Proot: Runs a full Linux distro inside a container. More compatibility, but heavier.

----------------------------------------------------------------------------------------------------------------------

Requirements:

Android 8 or higher

Termux installed from GitHub 

(NOT F-droid Version)

(NOT Google Play Version)

Termux-X11 installed from Github

At least 4 GB free storage

6-8 GB RAM recommended for smooth desktop use

----------------------------------------------------------------------------------------------------------------------

Step 1. Setting up Android

Developer Settings will be Located in "Android settings/Developer" 

To get Developer Settings to Show go to The Android Build Number Located in "Android Settings/About Phone/Software Information

If You dont See This Setting Then Your Phone Does Not Support It

Enable "disable child process restrictions"

This Setting Allows Termux to Run in the Background

----------------------------------------------------------------------------------------------------------------------

Step 2. Download and Install Termux & Termux-X11

Download Termux From https://github.com/termux/termux-app/releases/tag/v0.118.3

Download Termux-x11 From https://github.com/termux/termux-x11/releases/tag/nightly

Then go to Downloads Folder 

Select Termux to Install the app, Do The Same for Termux-X11

----------------------------------------------------------------------------------------------------------------------

Step 3. Setting Up Termux

to start with the commands

----------------------------------------------------------------------------------------------------------------------

This Command Sets up the Storage for Termux

1: termux-setup-storage

This Command Sets up the Repos

2: termux-change-repo

Click Enter Two Times

3: pkg update

4: pkg upgrade

----------------------------------------------------------------------------------------------------------------------

This Command Installs the Repos

5: pkg install x11-repo tur-repo root-repo

----------------------------------------------------------------------------------------------------------------------

This Command Installs the File Grabers

6: pkg install curl wget git

----------------------------------------------------------------------------------------------------------------------

This Command Installs the Desktop Environmet

7: pkg install xfce4 xfce4-goodies termux-x11-nightly

----------------------------------------------------------------------------------------------------------------------

These are Needed Programs to install

8: pkg install florence code-oss firefox ark

9: pkg install neofetch xorgproto nano

10: pkg install termux-exec clang

----------------------------------------------------------------------------------------------------------------------

These Commands is to Install Audio

11: pkg install pulseaudio

12: pulseaudio --start

----------------------------------------------------------------------------------------------------------------------

Then Finaly the Launch Command

termux-x11 :0 -xstartup "dbus-launch --exit-with-session xfce4-session"

And Thus a Native Termux Desktop Environment

![Screenshot_20260216_152457_TermuxX11](https://github.com/user-attachments/assets/f34eae2a-1ea6-4866-b082-87ddedc9832b)

if you want the wallpaper here it is

https://www.deviantart.com/jesuisnerd/art/Minimalist-Arch-Linux-Wallpaper-1920x1200-297370344

----------------------------------------------------------------------------------------------------------------------

Bonus program

I Know the Title Does Say no Scripts But This Program is an Exception to Termux

WOW64 is xow64 but wine to run .exe programs in termux

This Commnads is to Install WOW64

1: cd $HOME && rm -rf ~/xow64 && wget https://github.com/ar37-rs/xow64-wine/raw/refs/heads/main/xow64 && chmod +x ~/xow64

2: ~/xow64 install

3: ~/xow64 r winecfg

use ( r ) to run programs

Now Wine is Installed
