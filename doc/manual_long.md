| /opt/piget/samba/addToStartup      |                               |
|:-----------------------------------|:------------------------------|
| Info                               | [beta] [service] [systemctl]  |
| Description                        | Samba will be start on boot   |
| Usage                              | /opt/piget/samba/addToStartup |
| 1. Add samba at startup            |                               |
| 1. Samba will be launch at startup |                               |

| /opt/piget/samba/copy                       |                                               |
|:--------------------------------------------|:----------------------------------------------|
| Info                                        | [beta] [samba] [backup]                       |
| Description                                 | Copy a configuration to /etc/samba/smb.conf   |
| Usage                                       | /opt/piget/samba/copy file                    |
| Example                                     | /opt/piget/samba/copy /user/config/samba.conf |
| Arguments                                   | 1:settings,                                   |
| Variables                                   | settings=$1, name=$(/show/name),              |
| 1. [SAMBA] $settings -> /etc/samba/smb.conf |                                               |
| 1. $settings doesnt exists                  |                                               |

| /opt/piget/samba/download            |                                                                        |
|:-------------------------------------|:-----------------------------------------------------------------------|
| Info                                 | [beta] [wget] [github] [backup]                                        |
| Description                          | Download a configuration on github                                     |
| Usage                                | /opt/piget/samba/download pigetnet/smb mpd                             |
| Arguments                            | 1:repo, 2:sambaconf,                                                   |
| Variables                            | repo=$1, sambaconf=$2,                                                 |
| System                               | /system/downloadGithubFile "$repo" "$sambaconf" "/etc/samba/smb.conf", |
| 1. [SAMBA] Download $repo/$sambaconf |                                                                        |

| /opt/piget/samba/install                                              |                                                                                                                         |
|:----------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------|
| Info                                                                  | [beta] [samba] [install]                                                                                                |
| Description                                                           | Install samba and samba tools and set a default password (pi:raspberry)                                                 |
| Usage                                                                 | /opt/piget/samba/install                                                                                                |
| Softwares                                                             | samba, samba-common-bin, smbclient,                                                                                     |
| Modules                                                               | /do/samba/password $LOGIN $PASS,                                                                                        |
| System                                                                | /system/install samba, /system/install samba-common-bin, /system/install smbclient, /system/makedir /user/config/samba, |
| 1. [SAMBA] Install Windows File Sharing                               |                                                                                                                         |
| 4. [User] $LOGIN added                                                |                                                                                                                         |
| 5. [Password] $PASS added                                             |                                                                                                                         |
| 6. Change password with /do/samba/setupPassword or /do/samba/password |                                                                                                                         |

| /opt/piget/samba/isNameOnly   |                                                            |
|:------------------------------|:-----------------------------------------------------------|
| Info                          | [beta] [samba] [variable]                                  |
| Description                   | Check if samba shares something                            |
| Usage                         | /opt/piget/samba/isNameOnly                                |
| Variables                     | checkConfig=$(cat /etc/samba/smb.conf |grep "path"|wc -l), |

| /opt/piget/samba/listUsers   |                                 |
|:-----------------------------|:--------------------------------|
| Info                         | [beta] [samba] [list] [pdbedit] |
| Description                  | Display samba users             |
| Usage                        | /opt/piget/samba/listUsers      |

| /opt/piget/samba/load                               |                                                   |
|:----------------------------------------------------|:--------------------------------------------------|
| Info                                                | [beta] [samba] [sync]                             |
| Description                                         | Copy smb.conf from /user to current configuration |
| Usage                                               | /opt/piget/samba/load                             |
| Example                                             | /opt/piget/samba/load                             |
| System                                              | /system/restart samba,                            |
| 1. [SAMBA] - Reload saved configuration             |                                                   |
| 1. You must first backup your current configuration |                                                   |
| 2. Type : /do/samba/save                            |                                                   |

| /opt/piget/samba/mount            |                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:----------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Info                              | [beta] [mount] [cifs]                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Description                       | Mount a samba share on your Raspberry Pi                                                                                                                                                                                                                                                                                                                                                                                                         |
| Usage                             | /opt/piget/samba/mount source destination or /opt/piget/samba/mount source destination username password                                                                                                                                                                                                                                                                                                                                         |
| Example                           | /opt/piget/samba/mount \\\\madnerd\\piget /media/madnerd/piget or /opt/piget/samba/mount \\\\madnerd\\piget /media/madnerd/piget pi raspberry                                                                                                                                                                                                                                                                                                    |
| Arguments                         | 1:local  ip, 1:uncpath, 2:dir, 1:uncpath, 2:dir, 3:user, 4:password,                                                                                                                                                                                                                                                                                                                                                                             |
| Variables                         | local  ip=$1, OIFS=$IFS, IFS=$OIFS, stat=$?, uncpath=$1, dir=$2, uncpath=$1, dir=$2, user=$3, password=$4, host=$(echo $uncpath|grep -o -P '(?<=\\\\).*(?=\\)'), uncpath=$(echo $uncpath|sed "s/$host/$host.local/"), mount -t cifs $uncpath $dir -o user=$user,password=$password > /tmp/mountsmb.log 2>&1, error=$?, result=$(cat /tmp/mountsmb.log|head -n 1|grep -o '[0-9]*'), mount -t cifs $uncpath $dir -o user=$user,password=$password, |
| System                            | /system/makedir $dir,                                                                                                                                                                                                                                                                                                                                                                                                                            |
| 1. [SAMBA] Mount $uncpath on $dir |                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| 1. Already mount, remount         |                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| 2. Remount failed                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| 3. Invalid username or password   |                                                                                                                                                                                                                                                                                                                                                                                                                                                  |

| /opt/piget/samba/password              |                                                                                   |
|:---------------------------------------|:----------------------------------------------------------------------------------|
| Info                                   | [beta] [smbpasswd]                                                                |
| Description                            | Change password for an user or by default pi                                      |
| Usage                                  | /opt/piget/samba/password password or /opt/piget/samba/password username password |
| Example                                | /opt/piget/samba/password badPassword or /opt/piget/samba/password pi badPassword |
| Arguments                              | 1:username, 2:password, 1:password,                                               |
| Variables                              | username=$1, password=$2, password=$1, sambaUsers=$(/do/samba/listUsers),         |
| Modules                                | sambaUsers=$(/do/samba/listUsers),                                                |
| 1. [SAMBA] $username : PASSWORD        |                                                                                   |
| 1. The user must exists on the system! |                                                                                   |
| 2. no Samba users                      |                                                                                   |
| 3. Password changed                    |                                                                                   |

| /opt/piget/samba/README.MD   |                        |
|:-----------------------------|:-----------------------|
| Info                         | [alpha] [undocumented] |

| /opt/piget/samba/removeFromStartup   |                                    |
|:-------------------------------------|:-----------------------------------|
| Info                                 | [beta] [service] [systemctl]       |
| Description                          | Samba will not start at boot       |
| Usage                                | /opt/piget/samba/removeFromStartup |
| 1. Disable samba at startup          |                                    |
| 1. Samba will be launch at startup   |                                    |

| /opt/piget/samba/restart   |                             |
|:---------------------------|:----------------------------|
| Info                       | [release] [samba] [service] |
| Description                | Restart samba services      |
| Usage                      | /opt/piget/samba/restart    |
| System                     | /system/restart samba,      |

| /opt/piget/samba/save                   |                                               |
|:----------------------------------------|:----------------------------------------------|
| Info                                    | [beta] [samba] [backup]                       |
| Description                             | Save current configuration to /boot and /user |
| Usage                                   | /opt/piget/samba/save                         |
| 1. [SAMBA] - Save current configuration |                                               |

| /opt/piget/samba/settings   |                                                                                          |
|:----------------------------|:-----------------------------------------------------------------------------------------|
| Info                        | [beta] [samba] [interactive]                                                             |
| Description                 | Modify /etc/samba/smb.conf with nano editor                                              |
| Usage                       | /opt/piget/samba/settings                                                                |
| Variables                   | md5smb_before=$(md5sum /etc/samba/smb.conf), md5smb_after=$(md5sum /etc/samba/smb.conf), |
| Modules                     | /do/samba/restart,                                                                       |
| 1. Edit /etc/samba/smb.conf |                                                                                          |
| 1. Reload configuration     |                                                                                          |

| /opt/piget/samba/setupPassword         |                                                                                             |
|:---------------------------------------|:--------------------------------------------------------------------------------------------|
| Info                                   | [beta] [smbpasswd] [interactive]                                                            |
| Description                            | Change password for an user or by default pi (interactive)                                  |
| Usage                                  | /opt/piget/samba/setupPassword password or /opt/piget/samba/setupPassword username password |
| Example                                | /opt/piget/samba/setupPassword raspberry or /opt/piget/samba/setupPassword pi raspberry     |
| Arguments                              | 1:username,                                                                                 |
| Variables                              | username=$1, sambaUsers=$(/do/samba/listUsers),                                             |
| Modules                                | sambaUsers=$(/do/samba/listUsers), /do/samba/restart,                                       |
| 1. [SAMBA] $username : PASSWORD        |                                                                                             |
| 1. The user must exists on the system! |                                                                                             |
| 2. no Samba users                      |                                                                                             |
| 3. Password changed                    |                                                                                             |

| /opt/piget/samba/shareAll            |                                               |
|:-------------------------------------|:----------------------------------------------|
| Info                                 | [beta] [samba] [danger] [share]               |
| Description                          | Share the entire SDcard (use it with caution) |
| Usage                                | /opt/piget/samba/shareAll                     |
| Example                              | /opt/piget/samba/shareAll                     |
| Variables                            | sambaName=$(/show/smbGetName),                |
| Modules                              | cp /do/samba/conf/all /etc/samba/smb.conf,    |
| 1. [SAMBA] share everything          |                                               |
| 1. [WARNING] This is highly unsecure |                                               |
| 2. \\\\$sambaName\sd --> SD card     |                                               |

| /opt/piget/samba/shareNothing   |                                                                                                                         |
|:--------------------------------|:------------------------------------------------------------------------------------------------------------------------|
| Info                            | [beta] [samba] [share]                                                                                                  |
| Description                     | Share nothing but keep netbios name (will do nothing if this is already the case)                                       |
| Usage                           | /opt/piget/samba/shareNothing                                                                                           |
| Example                         | /opt/piget/samba/shareNothing                                                                                           |
| Variables                       | isNeeded=$(grep -v -F -x -f /do/samba/conf/name /etc/samba/smb.conf|wc -l), sambaName=$(/show/smbGetName),              |
| Modules                         | isNeeded=$(grep -v -F -x -f /do/samba/conf/name /etc/samba/smb.conf|wc -l), cp /do/samba/conf/name /etc/samba/smb.conf, |
| 1. [SAMBA] - Share nothing      |                                                                                                                         |
| 1. Already done                 |                                                                                                                         |

| /opt/piget/samba/sharePiget         |                                              |
|:------------------------------------|:---------------------------------------------|
| Info                                | [beta] [samba] [share]                       |
| Description                         | Share /opt/piget /opt/user and /boot/piget   |
| Usage                               | /opt/piget/samba/sharePiget                  |
| Example                             | /opt/piget/samba/sharePiget                  |
| Variables                           | sambaName=$(/show/smbGetName),               |
| Modules                             | cp /do/samba/conf/piget /etc/samba/smb.conf, |
| 1. [SAMBA] share Piget Folders      |                                              |
| 1. \\\\$sambaName\piget --> Modules |                                              |
| 2. \\\\$sambaName\user --> User     |                                              |
| 3. \\\\$sambaName\boot --> SD card  |                                              |

| /opt/piget/samba/shareUser   |                                                |
|:-----------------------------|:-----------------------------------------------|
| Info                         | [beta] [samba] [share]                         |
| Description                  | Share /opt/user (user folder)                  |
| Usage                        | /opt/piget/samba/shareUser                     |
| Example                      | /opt/piget/samba/shareUser                     |
| Modules                      | cp -v /do/samba/conf/user /etc/samba/smb.conf, |

| /opt/piget/samba/shareWeb   |                                               |
|:----------------------------|:----------------------------------------------|
| Info                        | [beta] [samba] [share]                        |
| Description                 | Share /var/www (using www-data as user)       |
| Usage                       | /opt/piget/samba/shareWeb                     |
| Example                     | /opt/piget/samba/shareWeb                     |
| Modules                     | cp -v /do/samba/conf/web /etc/samba/smb.conf, |

| /opt/piget/samba/start   |                            |
|:-------------------------|:---------------------------|
| Info                     | [release] [samba] [init.d] |
| Description              | Start samba services       |
| Usage                    | /opt/piget/samba/start     |

| /opt/piget/samba/status   |                               |
|:--------------------------|:------------------------------|
| Info                      | [release] [samba] [smbstatus] |
| Description               | Display status of samba share |
| Usage                     | /opt/piget/samba/status       |

| /opt/piget/samba/stop   |                            |
|:------------------------|:---------------------------|
| Info                    | [release] [samba] [init.d] |
| Description             | Stop samba services        |
| Usage                   | /opt/piget/samba/stop      |

| /opt/piget/samba/unmount   |                                    |
|:---------------------------|:-----------------------------------|
| Info                       | [beta] [umount]                    |
| Description                | Unmount a samba share              |
| Usage                      | /opt/piget/samba/unmount directory |
| Example                    | /opt/piget/samba/unmount directory |
| Arguments                  | 1:dir,                             |
| Variables                  | dir=$1, errorLevel=$?,             |
| 1. [SAMBA] unmount $dir    |                                    |
| 1. Successfuly unmount     |                                    |
| 2. Unmount failed          |                                    |
| 3. $dir is not mounted     |                                    |
| 4. $dir doesnt exists      |                                    |

| /opt/piget/samba/userConnected   |                                                     |
|:---------------------------------|:----------------------------------------------------|
| Info                             | [beta] [samba] [smbstatus] [boolean] [return]       |
| Description                      | Show if a user is connected to samba share          |
| Usage                            | /opt/piget/samba/userConnected                      |
| Variables                        | status=$(smbstatus|grep "Locked files:"|tail -n 1), |

