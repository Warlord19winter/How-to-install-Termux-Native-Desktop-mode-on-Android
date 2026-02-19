# How-to-install-Termux-Native-Desktop-mode-on-Android

In This Guide on Termux It Will Cover Only Github Version of Termux
----------------------------------------------------------------------------------------------------------------------

The Best Way to use Termux

No Proot/ No Chroot/ No Ai/ No Scripts

Straight Native Termux Desktop Mode

Requirements:
----------------------------------------------------------------------------------------------------------------------

Android 8 or higher

Termux installed from GitHub 

(NOT F-droid Version)

(NOT Google Play Version)

Termux-X11 installed from Github

At least 4 GB free storage

6-8 GB RAM recommended for smooth desktop use

----------------------------------------------------------------------------------------------------------------------

What Does Some of These Things Mean
----------------------------------------------------------------------------------------------------------------------

Phantom Process Killer Issue
----------------------------------------------------------------------------------------------------------------------

Phantom Process Killer in Android 12+ is a system feature that terminates background processes, particularly those spawning more than 32 child processes (a combined limit across all apps), often causing Termux to crash with the error [Process completed (signal 9) - press Enter]. 

This issue affects Termux, Andronix, and similar apps that run Linux environments or background services. The killer is triggered by excessive CPU usage or process count, leading to unexpected app termination. 

How to Fix It
For Non-Rooted Devices (Using ADB)
Enable Developer Options by tapping Build Number 7 times in Settings > About Phone. 
Enable USB Debugging and Wireless Debugging. 
Use a PC or Termux with android-tools to run:
adb shell "settings put global settings_enable_monitor_phantom_procs false"

For older Android versions (12), use:
adb shell "/system/bin/device_config set_sync_disabled_for_tests persistent"
adb shell "/system/bin/device_config put activity_manager max_phantom_processes 2147483647"

Reboot your device.
For Rooted Devices
Use Termux with root access (su) and run:

su -c "settings put global settings_enable_monitor_phantom_procs false"

Or for Android 12:

su -c "/system/bin/device_config set_sync_disabled_for_tests persistent"
su -c "/system/bin/device_config put activity_manager max_phantom_processes 2147483647"

Reboot after.

For Android 14+
Go to Settings > Developer Options > Disable child process restrictions (if available). 

What is The Commands Mean

----------------------------------------------------------------------------------------------------------------------

termux-setup-storage
----------------------------------------------------------------------------------------------------------------------

termux-setup-storage is a command used to grant Termux access to your Android device's shared storage, enabling it to interact with files in directories like Downloads, Pictures, and Documents. 

Run the command in Termux: termux-setup-storage
When prompted, tap "Allow" in the Android permissions dialog to grant access. 
This creates a ~/storage directory in your Termux home folder, containing symbolic links to key storage locations:
~/storage/shared → Root of shared storage (/sdcard)
~/storage/downloads → Your Downloads folder
~/storage/pictures → Pictures from all apps
~/storage/music → Audio files
~/storage/movies → Video files
~/storage/external → Termux-private folder on external storage (if available)

termux-Change-repo
----------------------------------------------------------------------------------------------------------------------

termux-change-repo is the official utility in Termux used to switch between different mirrors for the package repository.  It helps resolve issues like "repository under maintenance," slow downloads, or broken mirrors by allowing you to select a faster or more reliable source. 

Run the command:
termux-change-repo

The tool presents a menu to choose which repositories (e.g., main, x11, root) to update.
Select mirrors like BFSU, Grimler, or Fosshost using arrow keys and the spacebar. 
Confirm with Enter — it automatically updates the sources.list files. 
After switching, run:
pkg update && pkg upgrade

to refresh and update packages. 

pkg Update && Pkg Upgrade
----------------------------------------------------------------------------------------------------------------------

pkg update && pkg upgrade is the standard command sequence to keep Termux up to date. 

Run pkg update to refresh the package list from the repositories.
Follow with pkg upgrade to install the latest versions of all installed packages.
Use pkg update && pkg upgrade -y to automatically confirm prompts with -y, saving time. 

pkg install x11-repo root-repo tur-repo
----------------------------------------------------------------------------------------------------------------------

x11-repo: Installs the X11 package repository, enabling access to X11-related packages (like termux-x11-nightly, xwayland, and desktop environments such as XFCE4) for running graphical Linux applications on Android.  This is required to use Termux X11.

root-repo: Enables access to packages that require root privileges on Android.  These packages are not available in the standard Termux repository due to Android's security model. 

tur-repo: This is not a standard or official Termux repository.  It appears to be a typo or confusion with unstable-repo (for experimental packages) or its-pointless.github.io (a popular community repository). The tur-repo package does not exist in official Termux repositories and may cause errors. Use unstable-repo if you need unstable packages

pkg Install Git Wget Curl
----------------------------------------------------------------------------------------------------------------------

To install git, wget, and curl on Termux, run the following command in your Termux terminal:

pkg install git wget curl -y

This command installs all three packages:

git: For version control and interacting with repositories (e.g., GitHub). 

wget: A command-line utility for downloading files from the web. 

curl: A tool to transfer data using various protocols (HTTP, HTTPS, FTP, etc.).

pkg install xfce4 xfce4-goodies termux-x11-nightly
----------------------------------------------------------------------------------------------------------------------

To install XFCE4, XFCE4 goodies, and Termux-X11 Nightly on Termux, follow these steps:

Enable the X11 repository:
pkg install x11-repo

Install XFCE4 desktop environment and additional packages:
pkg install xfce4 xfce4-goodies

Install Termux-X11 Nightly app:
Download the APK from the official GitHub releases page: https://github.com/termux/termux-x11/releases
Install it on your Android device (requires sideloading). 

Start the XFCE4 session:
Launch the Termux:X11 app on your Android device.

In Termux, run:
termux-x11 :1 -xstartup "dbus-launch --exit-with-session xfce4-session"

This command starts the XFCE4 desktop environment via the X11 server. 
Note: Ensure you have dbus installed (pkg install dbus) for session management.  If you encounter issues, delete the .ICEauthority file in your home directory 

(rm -f ~/.ICEauthority) and retry. 

pkg install florence code-oss firefox ark
----------------------------------------------------------------------------------------------------------------------

The commands pkg install florence code-oss firefox ark in Termux are used to install specific software packages from Termux's package repository:

pkg install florence: Installs Florence, a virtual on-screen keyboard for Android, useful for touch-based input when using Termux with desktop environments or remote access.

pkg install code-oss: Installs Code-OSS, the open-source version of Visual Studio Code, available via the Termux User Repository (TUR).  It includes telemetry but can be configured to disable it by default.

pkg install firefox: Installs Firefox browser. This requires the x11-repo to be enabled for GUI support (e.g., via VNC or Termux:X11).

pkg install ark: Installs Ark, a lightweight, fast, and feature-rich file manager for Linux, suitable for managing files in Termux. 

termux-x11 :0 -xstartup "dbus-launch --exit-with-session xfce4-session"
----------------------------------------------------------------------------------------------------------------------

Termux-X11 works reliably when launching XFCE4 directly from Termux without using chroot or proot-distro.  The command:

env DISPLAY=:0 dbus-launch --exit-with-session xfce4-session

is the standard and recommended way to start the XFCE desktop environment in Termux when using Termux-X11. 

Key Points:
Ensure Termux-X11 is running: Start the Termux-X11 app with termux-x11 :0 & in the Termux terminal. 

Set the correct DISPLAY: Use export DISPLAY=:0 before launching the session. 

Use dbus-launch: This is required for proper session management in Termux-X11. However, some users report dbus-launch fails due to environment issues. 

If dbus-launch fails:
Replace the command with:

env DISPLAY=:0 xfce4-session &> /dev/null 2>&1

This bypasses dbus-launch entirely and often resolves connection issues, especially on newer Android versions or certain devices.

WOW64 XOW64
----------------------------------------------------------------------------------------------------------------------

XoW64-Wine is a preconfigured setup for running 32-bit Windows applications on ARM64 Android devices using Termux, combining Wine-WoW64 and Box64 without requiring root access. 

Key Features:
Wine Version: 10.12 staging (latest stable). 
Box64 Version: 0.3.7.

Supported Environments: Termux with glibc or proot (no root required). 

GPU Support: Full OpenGL/Vulkan via virgl, panfrost, turnip, or llvmpipe drivers. 

Desktop Mode: Run Windows apps in a virtual desktop using xfce4 via termux-x11. 

Installation:
pkg install wget

cd $HOME && rm -rf ~/xow64 && wget https://github.com/ar37-rs/xow64-wine/raw/refs/heads/main/xow64 && chmod +x ~/xow64

~/xow64 install

Basic Usage:
Launch Wine in desktop mode: ~/xow64 s
Run an .exe: ~/xow64 r app_name.exe
Configure screen size: ~/xow64 desk-size 1024x768

Quit Wine: ~/xow64 q 

Graphics & Performance:
Use virgl (virpipe) for best compatibility on Android 10+ with Vulkan 1.1+. 

Enable dxvk-proton for better Direct3D performance: ~/xow64 vkd3d=true

For Mali GPUs (G310+, G610, G710), use driver=panfrost with mmap32=false. 

Dosbox
----------------------------------------------------------------------------------------------------------------------

DOSBox is available in Termux through the x11-repo package repository, which provides graphical Linux applications for Android.  To install DOSBox in Termux:

Install Termux from F-Droid (not Google Play, as the Play Store version is outdated). 
Update packages and add the x11-repo:

pkg upgrade -y

pkg install x11-repo -y

Install DOSBox and a VNC server to view the graphical interface:

pkg install dosbox -y

----------------------------------------------------------------------------------------------------------------------

Step 1. Setting up Android

To get Developer Settings to Show go to The Android Build Number Located in "Android Settings/About Phone/Software Information

![ResizedImage_2026-02-17_15-15-18_1388](https://github.com/user-attachments/assets/c37b3062-d0ca-49e8-95a5-47db1733c12a)

![1001050516](https://github.com/user-attachments/assets/db32f979-a717-4adb-8208-435dfbb1c398)

![ResizedImage_2026-02-17_15-13-59_1111](https://github.com/user-attachments/assets/616a22e0-de5d-4ba1-8c9a-04e777fbca6f)

Click the Build Number 3 or More Times to Enable Developer settings

Developer Settings will be Located in "Android settings/Developer"

![ResizedImage_2026-02-17_15-29-57_2421](https://github.com/user-attachments/assets/fce5ae3b-387b-4ec0-84f5-b3d8ce5758ec)

The go to the Bottom of Developer Settings

![ResizedImage_2026-02-17_15-20-49_5293](https://github.com/user-attachments/assets/4febf4c7-81ba-4605-8602-02ea2bfbfe5f)


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

Use the Arrow keys up/down to select
then hit Spacebar

or press enter twice

Termux Will Ask You to Choose From Mirror Group, or Single Mirror

Reccomended Choose Mirror Group so You Don't Have no Issues With The Repo's

Single Mirror Gives you The Choice Of Differnt Repo's

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

10: pkg install termux-exec clang inxi

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

Bonus programs

This Command Installs Dosbox

pkg install dosbox

In the Config for Dosbox Paste This into the Text File at the Bottom

mount c /data/data/com.termux/files/home/Downloads
C:

Now Dosbox is Install

----------------------------------------------------------------------------------------------------------------------

I Know the Title Does Say no Scripts But This Program is an Exception to Termux

WOW64 is xow64 but wine to run .exe programs in termux

This Commnads is to Install WOW64

1: cd $HOME && rm -rf ~/xow64 && wget https://github.com/ar37-rs/xow64-wine/raw/refs/heads/main/xow64 && chmod +x ~/xow64

2: ~/xow64 install

3: ~/xow64 r winecfg

use ( r ) to run programs

Now Wine is Installed
