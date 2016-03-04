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

| /do/samba/load                          |                        |
|:----------------------------------------|:-----------------------|
| Info                                    | [alpha] [undocumented] |
| System                                  | /system/restart samba, |
| 1. [SAMBA] - Reload saved configuration |                        |

| /do/samba/mount              |                        |
|:-----------------------------|:-----------------------|
| Info                         | [alpha] [undocumented] |
| Arguments                    | 1:uncpath, 2:dir,      |
| Variables                    | uncpath=$1, dir=$2,    |
| 1. Mounting $uncpath at $dir |                        |

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

| /do/samba/public                                 |                                                                          |
|:-------------------------------------------------|:-------------------------------------------------------------------------|
| Info                                             | [alpha] [undocumented]                                                   |
| Softwares                                        | samba, smbclient,                                                        |
| System                                           | /system/install samba, /system/install smbclient, /system/restart samba, |
| 1. Public sharing (USE ONLY ON YOUR OWN NETWORK) |                                                                          |
| 2. Check Prerequisites                           |                                                                          |

| /do/samba/readme.md   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:----------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Info                  | [alpha] [undocumented]                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| Modules               | | /do/samba/addToStartup   |                              |, | /do/samba/copy   |                                             |, | Example          | /do/samba/copy /user/config/samba.conf      |, | /do/samba/download   |                                    |, | /do/samba/install   |                                                                         |, | /do/samba/isNameOnly   |                                 |, | /do/samba/listUsers   |                                 |, | /do/samba/load   |                        |, | /do/samba/mount   |                        |, | /do/samba/password   |                                                                     |, | Example              | /do/samba/password badPassword or /do/samba/password pi badPassword |, | /do/samba/public   |                        |, | /do/samba/remove   |                        |, | /do/samba/removeFromStartup   |                              |, | /do/samba/rename   |                         |, | /do/samba/restart   |                        |, | /do/samba/save   |                                               |, | Example          | /do/samba/save                                |, | /do/samba/secure   |                        |, | /do/samba/settings   |                        |, | /do/samba/setupPassword   |                                                                           |, | Example                   | /do/samba/setupPassword raspberry or /do/samba/setupPassword pi raspberry |, | /do/samba/shareAll   |                        |, | /do/samba/shareNothing   |                        |, | /do/samba/sharePiget   |                        |, | /do/samba/shareUser   |                        |, | /do/samba/shareWeb   |                        |, | /do/samba/start   |                             |, | /do/samba/status   |                               |, | /do/samba/stop   |                             |, | /do/samba/userConnected   |                                               |, |

| /do/samba/remove      |                        |
|:----------------------|:-----------------------|
| Info                  | [alpha] [undocumented] |
| 1. Uninstalling Samba |                        |

| /do/samba/removeFromStartup        |                              |
|:-----------------------------------|:-----------------------------|
| Info                               | [beta] [service] [systemctl] |
| Description                        | Samba will be start on boot  |
| Usage                              | /do/samba/removeFromStartup  |
| 1. Add samba at startup            |                              |
| 1. Samba will be launch at startup |                              |

| /do/samba/rename                  |                                                                   |
|:----------------------------------|:------------------------------------------------------------------|
| Info                              | [alpha] [undocumented]                                            |
| Usage                             | sambaRename newname                                               |
| Example                           | sambaRename raspberrypi                                           |
| Arguments                         | 1:NEW_HOSTNAME,                                                   |
| Variables                         | NEW_HOSTNAME=$(cat /boot/piget/config/name.txt), NEW_HOSTNAME=$1, |
| System                            | /system/restart samba,                                            |
| 1. Samba : $NEW_HOSTNAME          |                                                                   |
| 1. Name ==> /boot/config/name.txt |                                                                   |

| /do/samba/restart   |                        |
|:--------------------|:-----------------------|
| Info                | [alpha] [undocumented] |
| System              | /system/restart samba, |

| /do/samba/save                          |                                               |
|:----------------------------------------|:----------------------------------------------|
| Info                                    | [beta] [samba] [backup]                       |
| Description                             | Save current configuration to /boot and /user |
| Usage                                   | /do/samba/save                                |
| Example                                 | /do/samba/save                                |
| 1. [Samba] - Save current configuration |                                               |

| /do/samba/secure   |                        |
|:-------------------|:-----------------------|
| Info               | [alpha] [undocumented] |
| Modules            | /do/samba/restart,     |

| /do/samba/settings          |                        |
|:----------------------------|:-----------------------|
| Info                        | [alpha] [undocumented] |
| Modules                     | /do/samba/restart,     |
| 1. Edit /etc/samba/smb.conf |                        |

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

| /do/samba/shareAll                   |                                            |
|:-------------------------------------|:-------------------------------------------|
| Info                                 | [alpha] [undocumented]                     |
| Variables                            | sambaName=$(/show/smbGetName),             |
| Modules                              | cp /do/samba/conf/all /etc/samba/smb.conf, |
| 1. [SAMBA] share everything          |                                            |
| 1. [WARNING] This is highly unsecure |                                            |
| 2. \\\\$sambaName\sd --> SD card     |                                            |

| /do/samba/shareNothing     |                                                                                                                         |
|:---------------------------|:------------------------------------------------------------------------------------------------------------------------|
| Info                       | [alpha] [undocumented]                                                                                                  |
| Variables                  | isNeeded=$(grep -v -F -x -f /do/samba/conf/name /etc/samba/smb.conf|wc -l), sambaName=$(/show/smbGetName),              |
| Modules                    | isNeeded=$(grep -v -F -x -f /do/samba/conf/name /etc/samba/smb.conf|wc -l), cp /do/samba/conf/name /etc/samba/smb.conf, |
| 1. [SAMBA] - Share nothing |                                                                                                                         |
| 1. Already done            |                                                                                                                         |

| /do/samba/sharePiget                |                                              |
|:------------------------------------|:---------------------------------------------|
| Info                                | [alpha] [undocumented]                       |
| Variables                           | sambaName=$(/show/smbGetName),               |
| Modules                             | cp /do/samba/conf/piget /etc/samba/smb.conf, |
| 1. [SAMBA] share Piget Folders      |                                              |
| 1. \\\\$sambaName\piget --> Modules |                                              |
| 2. \\\\$sambaName\user --> User     |                                              |
| 3. \\\\$sambaName\boot --> SD card  |                                              |

| /do/samba/shareUser   |                                                                  |
|:----------------------|:-----------------------------------------------------------------|
| Info                  | [alpha] [undocumented]                                           |
| Modules               | cp -v /do/samba/conf/user /etc/samba/smb.conf, /do/samba/secure, |

| /do/samba/shareWeb   |                                               |
|:---------------------|:----------------------------------------------|
| Info                 | [alpha] [undocumented]                        |
| Modules              | cp -v /do/samba/conf/web /etc/samba/smb.conf, |

| /do/samba/start   |                             |
|:------------------|:----------------------------|
| Info              | [release] [samba] [service] |
| Description       | Start samba services        |
| Usage             | /do/samba/start             |

| /do/samba/status   |                               |
|:-------------------|:------------------------------|
| Info               | [release] [samba] [smbstatus] |
| Description        | Display status of samba share |
| Usage              | /do/samba/status              |

| /do/samba/stop   |                             |
|:-----------------|:----------------------------|
| Info             | [release] [samba] [service] |
| Description      | Stop samba services         |
| Usage            | /do/samba/stop              |

| /do/samba/userConnected   |                                                     |
|:--------------------------|:----------------------------------------------------|
| Info                      | [beta] [samba] [smbstatus] [boolean] [return]       |
| Description               | Show if a user is connected to samba share          |
| Usage                     | /do/samba/userConnected                             |
| Variables                 | status=$(smbstatus|grep "Locked files:"|tail -n 1), |

