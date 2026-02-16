# How-to-install-Termux-Native-Desktop-mode-on-Android
The Best Way to use Termux

No Proot/ No Chroot/ No Ai/ No Scripts

Straight Native Termux

Step 1. Setting up Android

 Developer Settings is Located in "Android settings/Developer" 
 
 This Setting Allows Termux to Run in the Background

To get Developer Settings to Show go to The Android Build Number Located in "Android Settings/About Phone/Software Information

If You dont See This Setting Then Your Phone Does Not Support It

Enable "disable child process restrictions"

Step 2. Download and Install Termux & Termux-X11

Download Termux & Termux-X11 From Github

Then go to Downloads Folder 
Select Termux to Install the app, Do The Same for Termux-X11

Step 3. Setting Up Termux

to start with the commands

1: termux-setup-storage

2: termux-change-repo

3: pkg update

4: pkg upgrade

5: pkg install x11-repo tur-repo root-repo

6: pkg install curl wget git

7: pkg install xfce4 xfce4-goodies termux-x11-nightly

8: pkg install florence code-oss firefox ark

then finaly the launch command

termux-x11 :0 -xstartup "dbus-launch --exit-with-session xfce4-session"

![Screenshot_20260216_151859_TermuxX11](https://github.com/user-attachments/assets/eed7d89d-1b03-4cf6-a11f-9950c1d0c33f)
