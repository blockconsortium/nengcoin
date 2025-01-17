# Mobile Mining on Android 64 bits phone (arm64) with UserLand App

This folder describe how to CPU mine Nengcoin (NENG) on 64 bits android phone (arm64). 


### Step 1: Install and setup UserLand app from Google Play Store

First install free "UserLand" app from google play store.  After installation, click Distribution 
"Debian", pick a username, password, and VNC password (which could be same password). You will enter 
a linux terminal inside UserLand app, which runs arm64 version of Debian 10 (Buster). 

Here we are recommending running through SSH (linux terminal) only, not VNC.  For linux GUI, it is much better to run remotely 
through putty and you can display all linux GUI software in windows 10 with a few mouse clicks of free software download and installs. See optional 
item at bottom of the parent page.

### Step 2: prepare UserLand

Type below commands in linux terminal inside Userland:

```
  sudo apt update
  sudo apt install wget ssh
  hostname -I
```

### Step 3: Remember IP of phone from above step, remote login from desktop computer

For windows 10 desktop machine, install a free software "PuTTY", login into phone with your
username/password picked at port 2022

A screen shot of putty was provided. 

For linux or MacOS,  you can remote login with ssh from command line at port 2022. For example 
IP = 192.168.1.98 with user "hlu" like below 
```
  ssh hlu@192.168.1.98 -p 2022
```

## Now you can run below commands from putty from windows 10 or ssh from MacOS or Linux
### Step 4: Prepare UserLand app Linux Terminal
First login into UserLand app linux terminal remotely, you should find that common linux command like "top", "uptime" does not work. 
Please run below for workaround for those issues:
```
  wget https://github.com/ShorelineCrypto/NengCoin/releases/download/v1.6.0.2/nengcoin_v1.6.0.2_android_userland_arm.tgz
  tar xvfz nengcoin_v1.6.0.2_android_userland_arm.tgz
  cd  Android_Userland_App/debian/arm64/
  bash prepare_userland.sh

```

After completion of above, logout and re-login into UserLand linux terminal, you should be able to use "top", "uptime" etc command. 


### Step 5: Install library files, wallet and cheetah_cpuminer
Please run below shell script in Userland Debian for installing dependencies and library files:
```
  bash prepare_neng.sh

```
The above step automatically download binary NENG wallet file and cheetah_cpuminer in current folder.

### Step 6: Optimize CPU mining with Cheetah_Cpuminer:

Run below to find cpu info and memory information:

```
  more /proc/cpuinfo
  top
```
 For quad core phone, 8 cpu threads were found. You can now optimize Cheetah_Cpuminer parameter to perform android mining. 
 
 For more information on CPU mining with cheetah_Cpuminer, please checkout:
https://github.com/ShorelineCrypto/cheetah_cpuminer

