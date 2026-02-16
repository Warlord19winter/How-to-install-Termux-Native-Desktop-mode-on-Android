# How-to-install-Termux-Native-Desktop-mode-on-Android
The Best Way to use Termux

No Proot/ No Chroot/ No Ai/ No Scripts

Straight Native Termux

Step 1. Setting up Android

Developer Settings will be Located in "Android settings/Developer" 

To get Developer Settings to Show go to The Android Build Number Located in "Android Settings/About Phone/Software Information

If You dont See This Setting Then Your Phone Does Not Support It

Enable "disable child process restrictions"

This Setting Allows Termux to Run in the Background

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

9: pkg install neofetch

Then Finaly the Launch Command

termux-x11 :0 -xstartup "dbus-launch --exit-with-session xfce4-session"

And Thus a Native Termux Desktop Environment

![Screenshot_20260216_152457_TermuxX11](https://github.com/user-attachments/assets/f34eae2a-1ea6-4866-b082-87ddedc9832b)
