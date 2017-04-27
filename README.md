# hostsFiles
Modified Hosts file. Uses a special version of hosts file forked from https://github.com/StevenBlack/hosts

Bans ads on websites:
fmovies.to

Bans additional websites:
behance.net

## Instructions for editing your hosts file.
[1.](https://github.com/foxtrot9/hostsFiles#1-location-of-your-hosts-file)  Find out location of your hosts file.

[2.](https://github.com/foxtrot9/hostsFiles#2-append-hoststxt-file) Append [hosts.txt](https://raw.githubusercontent.com/foxtrot9/hostsFiles/master/hosts.txt) file.

[3.](https://github.com/foxtrot9/hostsFiles#3-reloading-hosts-file) Reload `hosts` file.

## 1. Location of your hosts file
To modify your current `hosts` file, look for it in the following places and modify it with a text
editor.

**Mac OS X, iOS, Android, Linux**: `/etc/hosts` folder.

**Windows**: `%SystemRoot%\system32\drivers\etc\hosts` folder.

## 2. Append `hosts.txt` file.

### 2.0 Get a backup of your current hosts file.
**Windows**: `copy hosts hosts_backup.txt`

**Linux** + **MAC OS X**: `cp hosts hosts_backup.txt`

### 2.1 Change ownsership settings for file.

**Windows**:
1. Change properties of `hosts` file.

![1](https://raw.githubusercontent.com/foxtrot9/hostsFiles/master/Images/win1.png)


2. Select `Edit` option in `security` tab.

![2](https://raw.githubusercontent.com/foxtrot9/hostsFiles/master/Images/win2.png)


3. Allow `Modify` and `Write` for `Users`. Select apply.

![3](https://raw.githubusercontent.com/foxtrot9/hostsFiles/master/Images/win3.png)


**Linux** + **MAC OS X**: `ls -l hosts` Gives current ownership rights.

Change them to `sudo chmod +777 hosts`

### 2.2 Append hosts.txt file.
**Windows**: `type hosts.txt >> hosts`

**Linux** + **MAC OS X**: `cat hosts.txt >> hosts`

### 2.3 Change ownership rights back to normal.

**Windows**:
Follow [Section 2.1](https://github.com/foxtrot9/hostsFiles#21-change-ownsership-settings-for-file) and revert back changes done in last step.

**Linux** + **MAC OS X**: Say old rights were `644` which means `-rw-r--r--` in output of section 2.1.

```
sudo chmod -777 hosts
sudo chmod +644 hosts
```

## 3. Reloading hosts file
Your operating system will cache DNS lookups. You can either reboot or run the following commands to
manually flush your DNS cache once the new hosts file is in place.

#### Mac OS X
Open a Terminal and run:
```
sudo dscacheutil -flushcache;sudo killall -HUP mDNSResponder
```

#### Windows

|`makeHostsWindows.bat` BATCH file will create various alternate hosts files by combining and adding the gambling, porn, and social media extensions. You need to be connected to the Internet. This file REQUIRED installed Python 3.5.x runtime environment in Windows System. Launch this file as normal user.|
:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

|Run `updateHostsWindows.bat` BATCH file in Command Prompt with Administrator privileges in repository directory for easy update, replace hosts file and reload DNS cache in Windows System. You need to be connected to the Internet. This file REQUIRED installed Python 3.5.x runtime environment in Windows System.|
:---------------------------------------------------------------------------------------------------------------------------------------------------------------------|

|WARNING: Don't run these BAT files directly or from popup menu. You have been warned.|
:--------------------------------------------------------------------------------------

Open a Command Prompt in directory where are files from this repository:

**Windows XP**: Start -> Run -> `cmd`

**Windows Vista, 7**: Start Button -> type `cmd` -> right-click Command Prompt ->
"Run as Administrator"

**Windows 8**: Start -> Swipe Up -> All Apps -> Windows System -> right-click Command Prompt ->
"Run as Administrator"

**Windows 10**: Start Button -> type `cmd` -> right-click Command Prompt ->
"Run as Administrator"

and run command:
```
updateHostsWindows.bat
```

|If you want to use a huge hosts file by merging [hphosts](https://www.hosts-file.net) (NOT INCLUDED HERE) you need to DISABLE and STOP `Dnscache` service before you replace hosts file in Windows Systems. You have been warned.|
:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Open a Command Prompt with Administrator privileges and run once commands:

```
sc config "Dnscache" start= disabled
sc stop "Dnscache"
```

#### Linux
Open a Terminal and run with root privileges:

**Debian/Ubuntu** `sudo /etc/rc.d/init.d/nscd restart`

**Linux with systemd**: `sudo systemctl restart network.service`

**Fedora Linux**: `sudo systemctl restart NetworkManager.service`

**Arch Linux/Manjaro with Network Manager**: `sudo systemctl restart NetworkManager.service`

**Arch Linux/Manjaro with Wicd**: `sudo systemctl restart wicd.service`

**Others**: Consult [this wikipedia article](https://en.wikipedia.org/wiki/Hosts_%28file%29#Location_in_the_file_system).
