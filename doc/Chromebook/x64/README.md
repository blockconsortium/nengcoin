# Chrome OS on x86_64

This folder describe how to run a full node of Nengcoin (NENG) and to CPU mine NENG in Chromebook as Linux App.  Chrome OS v85 on x64 platform was tested. 
Any Chrome OS version v69 or later on x64 CPU should all work. 

Chrome OS v85 Linux (Beta) runs Debian 10 (Buster) in embedded linux in a container with close to full feature of linux for both CLI and GUI. 
Older version of Chrome OS run Debian 9 (Stretch). The below script and method was also tested on Debian 9 successfully and should all just work on Debian 9.
   

- Minimum hardware requirement: 2G memory chromebook with 3G additonal spare hard disk. 
- Software Required: Linux (Beta) turned on in Chrome OS

For CPU mining steps and optimization with cheetah_Cpuminer, please checkout: 
https://github.com/ShorelineCrypto/cheetah_cpuminer

## Turn on Linux Beta (Crostini)
Go to Chrome OS setting, turn on Linux (Beta).  If your chromebook does not have this option, it is not supported here for NENG CPU mining. 

For disk size in Linux Beta, we recommend to add 3G on top of recommended 5G by Google. So pick custom disk 8G as minimum selection. 

## Start linux Terminal

You can pin linux "Terminal" at menu bar. Download this tgz file to chromebook, drag the file from "Downloads" to "Linux files" folder in chromebook. 
Inside terminal, this file will be at your home directory.  

By default, Linux (Beta) or Crostini runs a container for Debian 10. Below has been tested to be working in both Debian 10 and Debian 9.  Run below commands to install all required files:

```
   tar xvfz nengcoin_v1.6.0.3_chromeos_x64.tgz
   cd Chromebook/x64/debian
   bash  prepare_neng.sh
```

After successfully completing above commands, NENG wallet file and Cheetah_Cpuminer will be downloaded at your current folder. You can move these files to whatever best location inside your "Linux files" folder by using either linux command line or Chromebook GUI drag and drop. 

## Crostini Ubuntu 18.04 Alternative

Ubuntu has better hardware and gaming support on x64 platform in linux. You can setup x64 penguin container using Ubuntu 18.04 to replace Debian 10 for Crostini. In case you runs a Ubuntu 18.04 container in Linux (Beta),  ubuntu 18.04 installation scripts folder is also provided with README file. 

## Linux Terminal CLI or Desktop GUI wallet for mining? 

For NENG cpu mining purpose, either CLI wallet or GUI QT wallet was tested working in Chromebook.  You can run either of the software
to run a full node and for the purpose of CPU mining. 

## run GUI QT wallet in Chromebook

 ```
 hlu@penguin:~$ cd  nengcoin_v1.6.0.0_ubuntu16.04
 hlu@penguin:~/nengcoin_v1.6.0.0_ubuntu16.04$ ./nengcoin-qt &
```

Above in linux terminal will pop NENG QT wallet in chromebook desktop.

## Copy the conf file and restart wallet
 QT wallet in penguin container may show no connections.  Copy the conf file with below command:

```
hlu@penguin:~$  cp nengcoin.conf ~/.nengcoin/
```

 Then restart the QT GUI wallet, NENG should start to sync. Note fully synced to latest block is required in order to CPU mining NENG with Cheetah_Cpuminer
 

## FAQ - Linux Terminal Basic Keyboard

Typing command line in linux terminal inside Chromebook is reasonably easy if you are familiar with linux command line on server or desktop. 

#### TAB key on auto filling
TAB key is powerful in linux command line.  Typing full word of file or folder names are inconvenient. 

Here is easier way with tab:
```
   cd  nengcoin_v1.6.0.0_ubuntu16.04

```
  Typing above long word in Chromebook is close to impossible. An easier way to do is:

```
   cd  nengc-finger push TAB key
```
After you push TAB afer word "nengc" , the chromebook linux terminal should behave like linux in server/desktop with the full file/folder name "nengcoin_v1.6.0.0_ubuntu16.04" auto populated for you. 

#### Arrow up or down key for history

The arrow up or down key is useful key if you want to repeat a command in recent history.  This is same as desktop/server linux terminal. 


## optional - "screen" command to run cheetah_cpuminer

"screen" is useful linux command for background running in linux, you can start screen session job in the Chromebook and detach. 
When you re-login into Chromebook, you can re-attach the screen session with a command.  Useful keyboards commands to be remembered:
####  start a screen session: type "screen" command in linux terminal
####  detach screen: Ctrl-A-D
####  re-attach screen: type "screen -r" command
####  re-attach specfic screen session when multiple sessions are running (say 3145.pts-1.localhost session):  screen -r 31
#### force re-attach if the screen session is open at another computer: screen -r 31 -d

  Inside screen, run below in cheetah to mine NENG, and detach screen session to leave it running in background:
```
   screen

   python main.py --interval 10 --cpu 6

   CTRL-A-D

```

You can let it run overnight until you pick up the Chromebook tomorrow for daily use. 



