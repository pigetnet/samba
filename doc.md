| /do/samba/addToStartup             |                              |
|:-----------------------------------|:-----------------------------|
| Info                               | [beta] [service] [systemctl] |
| Description                        | Samba will be start on boot  |
| Usage                              | /do/samba/addToStartup       |
| 1. Add samba at startup            |                              |
| 1. Samba will be launch at startup |                              |

| /do/samba/copy                              |                                             |
|:--------------------------------------------|:--------------------------------------------|
| Info                                        | [beta] [samba] [backup]                     |
| Description                                 | Copy a configuration to /etc/samba/smb.conf |
| Usage                                       | /do/samba/copy file                         |
| Example                                     | /do/samba/copy /user/config/samba.conf      |
| Arguments                                   | 1:settings,                                 |
| Variables                                   | settings=$1,                                |
| 1. [SAMBA] $settings -> /etc/samba/smb.conf |                                             |
| 1. $settings doesnt exists                  |                                             |

| /do/samba/download                   |                                                                        |
|:-------------------------------------|:-----------------------------------------------------------------------|
| Info                                 | [beta] [wget] [github] [backup]                                        |
| Description                          | Download a configuration on github                                     |
| Usage                                | /do/samba/download pigetnet/smb mpd                                    |
| Arguments                            | 1:repo, 2:sambaconf,                                                   |
| Variables                            | repo=$1, sambaconf=$2,                                                 |
| System                               | /system/downloadGithubFile "$repo" "$sambaconf" "/etc/samba/smb.conf", |
| 1. [SAMBA] Download $repo/$sambaconf |                                                                        |

| /do/samba/install                                                     |                                                                                     |
|:----------------------------------------------------------------------|:------------------------------------------------------------------------------------|
| Info                                                                  | [beta] [samba] [install]                                                            |
| Description                                                           | Install samba and samba tools and set a default password (pi:raspberry)             |
| Usage                                                                 | /do/samba/install                                                                   |
| Softwares                                                             | samba, samba-common-bin, smbclient,                                                 |
| Modules                                                               | /do/samba/password $LOGIN $PASS,                                                    |
| System                                                                | /system/install samba, /system/install samba-common-bin, /system/install smbclient, |
| 1. [SAMBA] Install Windows File Sharing                               |                                                                                     |
| 4. [User] $LOGIN added                                                |                                                                                     |
| 5. [Password] $PASS added                                             |                                                                                     |
| 6. Change password with /do/samba/setupPassword or /do/samba/password |                                                                                     |

| /do/samba/isNameOnly   |                                                            |
|:-----------------------|:-----------------------------------------------------------|
| Info                   | [beta] [samba] [variable]                                  |
| Description            | Check if samba shares something                            |
| Usage                  | /do/samba/isNameOnly                                       |
| Variables              | checkConfig=$(cat /etc/samba/smb.conf |grep "path"|wc -l), |

| /do/samba/listUsers   |                                 |
|:----------------------|:--------------------------------|
| Info                  | [beta] [samba] [list] [pdbedit] |
| Description           | Display samba users             |
| Usage                 | /do/samba/listUsers             |

| /do/samba/load                                      |                                                   |
|:----------------------------------------------------|:--------------------------------------------------|
| Info                                                | [beta] [samba] [sync]                             |
| Description                                         | Copy smb.conf from /user to current configuration |
| Usage                                               | /do/samba/load                                    |
| Example                                             | /do/samba/load                                    |
| System                                              | /system/restart samba,                            |
| 1. [SAMBA] - Reload saved configuration             |                                                   |
| 1. You must first backup your current configuration |                                                   |
| 2. Type : /do/samba/save                            |                                                   |

| /do/samba/mount                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:----------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Info                              | [beta] [mount] [cifs]                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Description                       | Mount a samba share on your Raspberry Pi                                                                                                                                                                                                                                                                                                                                                                                                         |
| Usage                             | /do/samba/mount source destination or /do/samba/mount source destination username password                                                                                                                                                                                                                                                                                                                                                       |
| Example                           | /do/samba/mount \\\madnerd\\piget  TODO /do/samba/mount TODO TODO TODO TODO                                                                                                                                                                                                                                                                                                                                                                      |
| Arguments                         | 1:local  ip, 1:uncpath, 2:dir, 1:uncpath, 2:dir, 3:user, 4:password,                                                                                                                                                                                                                                                                                                                                                                             |
| Variables                         | local  ip=$1, OIFS=$IFS, IFS=$OIFS, stat=$?, uncpath=$1, dir=$2, uncpath=$1, dir=$2, user=$3, password=$4, host=$(echo $uncpath|grep -o -P '(?<=\\\\).*(?=\\)'), uncpath=$(echo $uncpath|sed "s/$host/$host.local/"), mount -t cifs $uncpath $dir -o user=$user,password=$password > /tmp/mountsmb.log 2>&1, error=$?, result=$(cat /tmp/mountsmb.log|head -n 1|grep -o '[0-9]*'), mount -t cifs $uncpath $dir -o user=$user,password=$password, |
| System                            | /system/makedir $dir,                                                                                                                                                                                                                                                                                                                                                                                                                            |
| 1. [SAMBA] Mount $uncpath on $dir |                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| 1. Already mount, remount         |                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| 2. Remount failed                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| 3. Invalid username or password   |                                                                                                                                                                                                                                                                                                                                                                                                                                                  |

| /do/samba/password                     |                                                                           |
|:---------------------------------------|:--------------------------------------------------------------------------|
| Info                                   | [beta] [smbpasswd]                                                        |
| Description                            | Change password for an user or by default pi                              |
| Usage                                  | /do/samba/password password or /do/samba/password username password       |
| Example                                | /do/samba/password badPassword or /do/samba/password pi badPassword       |
| Arguments                              | 1:username, 2:password, 1:password,                                       |
| Variables                              | username=$1, password=$2, password=$1, sambaUsers=$(/do/samba/listUsers), |
| Modules                                | sambaUsers=$(/do/samba/listUsers), /do/samba/secure,                      |
| 1. [SAMBA] $username : PASSWORD        |                                                                           |
| 1. The user must exists on the system! |                                                                           |
| 2. no Samba users                      |                                                                           |
| 3. Password changed                    |                                                                           |

  
| /do/samba/removeFromStartup        |                              |
|:-----------------------------------|:-----------------------------|
| Info                               | [beta] [service] [systemctl] |
| Description                        | Samba will not start at boot |
| Usage                              | /do/samba/removeFromStartup  |
| 1. Disable samba at startup        |                              |
| 1. Samba will be launch at startup |                              |

| /do/samba/restart   |                             |
|:--------------------|:----------------------------|
| Info                | [release] [samba] [service] |
| Description         | Restart samba services      |
| Usage               | /do/samba/restart           |
| System              | /system/restart samba,      |

| /do/samba/save                          |                                               |
|:----------------------------------------|:----------------------------------------------|
| Info                                    | [beta] [samba] [backup]                       |
| Description                             | Save current configuration to /boot and /user |
| Usage                                   | /do/samba/save                                |
| 1. [SAMBA] - Save current configuration |                                               |

| /do/samba/settings          |                                                                                          |
|:----------------------------|:-----------------------------------------------------------------------------------------|
| Info                        | [beta] [samba] [interactive]                                                             |
| Description                 | Modify /etc/samba/smb.conf with nano editor                                              |
| Usage                       | /do/samba/settings                                                                       |
| Variables                   | md5smb_before=$(md5sum /etc/samba/smb.conf), md5smb_after=$(md5sum /etc/samba/smb.conf), |
| Modules                     | /do/samba/restart,                                                                       |
| 1. Edit /etc/samba/smb.conf |                                                                                          |
| 1. Reload configuration     |                                                                                          |

| /do/samba/setupPassword                |                                                                               |
|:---------------------------------------|:------------------------------------------------------------------------------|
| Info                                   | [beta] [smbpasswd] [interactive]                                              |
| Description                            | Change password for an user or by default pi (interactive)                    |
| Usage                                  | /do/samba/setupPassword password or /do/samba/setupPassword username password |
| Example                                | /do/samba/setupPassword raspberry or /do/samba/setupPassword pi raspberry     |
| Arguments                              | 1:username,                                                                   |
| Variables                              | username=$1, sambaUsers=$(/do/samba/listUsers),                               |
| Modules                                | sambaUsers=$(/do/samba/listUsers), /do/samba/secure,                          |
| 1. [SAMBA] $username : PASSWORD        |                                                                               |
| 1. The user must exists on the system! |                                                                               |
| 2. no Samba users                      |                                                                               |
| 3. Password changed                    |                                                                               |

| /do/samba/shareAll                   |                                               |
|:-------------------------------------|:----------------------------------------------|
| Info                                 | [beta] [samba] [danger] [share]               |
| Description                          | Share the entire SDcard (use it with caution) |
| Usage                                | /do/samba/shareAll                            |
| Example                              | /do/samba/shareAll                            |
| Variables                            | sambaName=$(/show/smbGetName),                |
| Modules                              | cp /do/samba/conf/all /etc/samba/smb.conf,    |
| 1. [SAMBA] share everything          |                                               |
| 1. [WARNING] This is highly unsecure |                                               |
| 2. \\\\$sambaName\sd --> SD card     |                                               |

| /do/samba/shareNothing     |                                                                                                                         |
|:---------------------------|:------------------------------------------------------------------------------------------------------------------------|
| Info                       | [beta] [samba] [share]                                                                                                  |
| Description                | Share nothing but keep netbios name (will do nothing if this is already the case)                                       |
| Usage                      | /do/samba/shareNothing                                                                                                  |
| Example                    | /do/samba/shareNothing                                                                                                  |
| Variables                  | isNeeded=$(grep -v -F -x -f /do/samba/conf/name /etc/samba/smb.conf|wc -l), sambaName=$(/show/smbGetName),              |
| Modules                    | isNeeded=$(grep -v -F -x -f /do/samba/conf/name /etc/samba/smb.conf|wc -l), cp /do/samba/conf/name /etc/samba/smb.conf, |
| 1. [SAMBA] - Share nothing |                                                                                                                         |
| 1. Already done            |                                                                                                                         |

| /do/samba/sharePiget                |                                              |
|:------------------------------------|:---------------------------------------------|
| Info                                | [beta] [samba] [share]                       |
| Description                         | Share /opt/piget /opt/user and /boot/piget   |
| Usage                               | /do/samba/sharePiget                         |
| Example                             | /do/samba/sharePiget                         |
| Variables                           | sambaName=$(/show/smbGetName),               |
| Modules                             | cp /do/samba/conf/piget /etc/samba/smb.conf, |
| 1. [SAMBA] share Piget Folders      |                                              |
| 1. \\\\$sambaName\piget --> Modules |                                              |
| 2. \\\\$sambaName\user --> User     |                                              |
| 3. \\\\$sambaName\boot --> SD card  |                                              |

| /do/samba/shareUser   |                                                |
|:----------------------|:-----------------------------------------------|
| Info                  | [beta] [samba] [share]                         |
| Description           | Share /opt/user (user folder)                  |
| Usage                 | /do/samba/shareUser                            |
| Example               | /do/samba/shareUser                            |
| Modules               | cp -v /do/samba/conf/user /etc/samba/smb.conf, |

| /do/samba/shareWeb   |                                               |
|:---------------------|:----------------------------------------------|
| Info                 | [beta] [samba] [share]                        |
| Description          | Share /var/www (using www-data as user)       |
| Usage                | /do/samba/shareWeb                            |
| Example              | /do/samba/shareWeb                            |
| Modules              | cp -v /do/samba/conf/web /etc/samba/smb.conf, |

| /do/samba/start   |                            |
|:------------------|:---------------------------|
| Info              | [release] [samba] [init.d] |
| Description       | Start samba services       |
| Usage             | /do/samba/start            |

| /do/samba/status   |                               |
|:-------------------|:------------------------------|
| Info               | [release] [samba] [smbstatus] |
| Description        | Display status of samba share |
| Usage              | /do/samba/status              |

| /do/samba/stop   |                            |
|:-----------------|:---------------------------|
| Info             | [release] [samba] [init.d] |
| Description      | Stop samba services        |
| Usage            | /do/samba/stop             |

| /do/samba/unmount       |                             |
|:------------------------|:----------------------------|
| Info                    | [beta] [umount]             |
| Description             | Unmount a samba share       |
| Usage                   | /do/samba/unmount directory |
| Example                 | /do/samba/unmount directory |
| Arguments               | 1:dir,                      |
| Variables               | dir=$1, errorLevel=$?,      |
| 1. [SAMBA] unmount $dir |                             |
| 1. Successfuly unmount  |                             |
| 2. Unmount failed       |                             |
| 3. $dir is not mounted  |                             |
| 4. $dir doesnt exists   |                             |

| /do/samba/userConnected   |                                                     |
|:--------------------------|:----------------------------------------------------|
| Info                      | [beta] [samba] [smbstatus] [boolean] [return]       |
| Description               | Show if a user is connected to samba share          |
| Usage                     | /do/samba/userConnected                             |
| Variables                 | status=$(smbstatus|grep "Locked files:"|tail -n 1), |

