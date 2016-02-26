| /opt/piget/samba/addToStartup      |                        |
|:-----------------------------------|:-----------------------|
| Info                               | [alpha] [undocumented] |
| 1. Add samba at startup            |                        |
| 1. Samba will be launch at startup |                        |

| /opt/piget/samba/customSettings   |                        |
|:----------------------------------|:-----------------------|
| Info                              | [alpha] [undocumented] |
| Arguments                         | 1:settings,            |
| Variables                         | settings=$1,           |

| /opt/piget/samba/download   |                                                                                                                |
|:----------------------------|:---------------------------------------------------------------------------------------------------------------|
| Info                        | [alpha] [undocumented]                                                                                         |
| Usage                       | sambaDownload dir                                                                                              |
| Example                     | sambaDownload pigetdev                                                                                         |
| Arguments                   | 1:sambaconf,                                                                                                   |
| Variables                   | sambaconf=$1,                                                                                                  |
| Modules                     | /do/samba/rename,                                                                                              |
| System                      | /system/autoBackup "/etc/samba/smb.conf", /system/downloadGithubFile "smb" "$sambaconf" "/etc/samba/smb.conf", |

| /opt/piget/samba/downloadCustom                               |                                                                                                                                                           |
|:--------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------|
| Info                                                          | [alpha] [undocumented]                                                                                                                                    |
| Usage                                                         | sambaDownloadCustom username repo file                                                                                                                    |
| Example                                                       | sambaDownloadCustom pigetnet smb piget                                                                                                                    |
| Softwares                                                     | samba,                                                                                                                                                    |
| Arguments                                                     | 1:username, 2:repo, 3:sambaconf,                                                                                                                          |
| Variables                                                     | username=$1, repo=$2, sambaconf=$3,                                                                                                                       |
| Modules                                                       | /do/samba/rename,                                                                                                                                         |
| System                                                        | /system/install samba, /system/autoBackup "/etc/samba/smb.conf", /system/downloadGithubFileCustom "$username" "$repo" "$sambaconf" "/etc/samba/smb.conf", |
| 1. Downloading samba configuration $username/$repo/$sambaconf |                                                                                                                                                           |

| /opt/piget/samba/install                                              |                                                                                     |
|:----------------------------------------------------------------------|:------------------------------------------------------------------------------------|
| Info                                                                  | [alpha] [undocumented]                                                              |
| Softwares                                                             | samba, samba-common-bin, smbclient,                                                 |
| Modules                                                               | /do/samba/password $LOGIN $PASS,                                                    |
| System                                                                | /system/install samba, /system/install samba-common-bin, /system/install smbclient, |
| 1. [SAMBA] Install Windows File Sharing                               |                                                                                     |
| 4. [User] $LOGIN added                                                |                                                                                     |
| 5. [Password] $PASS added                                             |                                                                                     |
| 6. Change password with /do/samba/setupPassword or /do/samba/password |                                                                                     |

| /opt/piget/samba/isNameOnly   |                                                            |
|:------------------------------|:-----------------------------------------------------------|
| Info                          | [alpha] [undocumented]                                     |
| Variables                     | checkConfig=$(cat /etc/samba/smb.conf |grep "path"|wc -l), |

| /opt/piget/samba/listUsers   |                            |
|:-----------------------------|:---------------------------|
| Info                         | [alpha] [undocumented]     |
| Softwares                    | smbclient,                 |
| System                       | /system/install smbclient, |

| /opt/piget/samba/load                   |                        |
|:----------------------------------------|:-----------------------|
| Info                                    | [alpha] [undocumented] |
| System                                  | /system/restart samba, |
| 1. [SAMBA] - Reload saved configuration |                        |

| /opt/piget/samba/mount       |                        |
|:-----------------------------|:-----------------------|
| Info                         | [alpha] [undocumented] |
| Arguments                    | 1:uncpath, 2:dir,      |
| Variables                    | uncpath=$1, dir=$2,    |
| 1. Mounting $uncpath at $dir |                        |

| /opt/piget/samba/password              |                                                                                   |
|:---------------------------------------|:----------------------------------------------------------------------------------|
| Info                                   | [beta] [smbpasswd]                                                                |
| Description                            | Change password for an user or by default pi                                      |
| Usage                                  | /opt/piget/samba/password password or /opt/piget/samba/password username password |
| Example                                | /opt/piget/samba/password badPassword or /opt/piget/samba/password pi badPassword |
| Arguments                              | 1:username, 2:password, 1:password,                                               |
| Variables                              | username=$1, password=$2, password=$1, sambaUsers=$(/do/samba/listUsers),         |
| Modules                                | sambaUsers=$(/do/samba/listUsers), /do/samba/secure,                              |
| 1. [SAMBA] $username : PASSWORD        |                                                                                   |
| 1. The user must exists on the system! |                                                                                   |
| 2. no Samba users                      |                                                                                   |
| 3. Password changed                    |                                                                                   |

| /opt/piget/samba/public                          |                                                                          |
|:-------------------------------------------------|:-------------------------------------------------------------------------|
| Info                                             | [alpha] [undocumented]                                                   |
| Softwares                                        | samba, smbclient,                                                        |
| System                                           | /system/install samba, /system/install smbclient, /system/restart samba, |
| 1. Public sharing (USE ONLY ON YOUR OWN NETWORK) |                                                                          |
| 2. Check Prerequisites                           |                                                                          |

| /opt/piget/samba/readme.md   |                        |
|:-----------------------------|:-----------------------|
| Info                         | [alpha] [undocumented] |

| /opt/piget/samba/remove   |                        |
|:--------------------------|:-----------------------|
| Info                      | [alpha] [undocumented] |
| 1. Uninstalling Samba     |                        |

| /opt/piget/samba/removeFromStartup   |                        |
|:-------------------------------------|:-----------------------|
| Info                                 | [alpha] [undocumented] |
| 1. Remove samba from startup         |                        |
| 1. Samba will not start at next boot |                        |

| /opt/piget/samba/rename           |                                                                   |
|:----------------------------------|:------------------------------------------------------------------|
| Info                              | [alpha] [undocumented]                                            |
| Usage                             | sambaRename newname                                               |
| Example                           | sambaRename raspberrypi                                           |
| Arguments                         | 1:NEW_HOSTNAME,                                                   |
| Variables                         | NEW_HOSTNAME=$(cat /boot/piget/config/name.txt), NEW_HOSTNAME=$1, |
| System                            | /system/restart samba,                                            |
| 1. Samba : $NEW_HOSTNAME          |                                                                   |
| 1. Name ==> /boot/config/name.txt |                                                                   |

| /opt/piget/samba/restart   |                        |
|:---------------------------|:-----------------------|
| Info                       | [alpha] [undocumented] |
| System                     | /system/restart samba, |

| /opt/piget/samba/save                   |                        |
|:----------------------------------------|:-----------------------|
| Info                                    | [alpha] [undocumented] |
| 1. [Samba] - Save current configuration |                        |

| /opt/piget/samba/secure   |                        |
|:--------------------------|:-----------------------|
| Info                      | [alpha] [undocumented] |
| Modules                   | /do/samba/restart,     |

| /opt/piget/samba/settings   |                        |
|:----------------------------|:-----------------------|
| Info                        | [alpha] [undocumented] |
| Modules                     | /do/samba/restart,     |
| 1. Edit /etc/samba/smb.conf |                        |

| /opt/piget/samba/setupPassword         |                                                                                             |
|:---------------------------------------|:--------------------------------------------------------------------------------------------|
| Info                                   | [beta] [smbpasswd] [interactive]                                                            |
| Description                            | Change password for an user or by default pi (interactive)                                  |
| Usage                                  | /opt/piget/samba/setupPassword password or /opt/piget/samba/setupPassword username password |
| Example                                | /opt/piget/samba/setupPassword raspberry or /opt/piget/samba/setupPassword pi raspberry     |
| Arguments                              | 1:username,                                                                                 |
| Variables                              | username=$1, sambaUsers=$(/do/samba/listUsers),                                             |
| Modules                                | sambaUsers=$(/do/samba/listUsers), /do/samba/secure,                                        |
| 1. [SAMBA] $username : PASSWORD        |                                                                                             |
| 1. The user must exists on the system! |                                                                                             |
| 2. no Samba users                      |                                                                                             |
| 3. Password changed                    |                                                                                             |

| /opt/piget/samba/shareAll            |                                               |
|:-------------------------------------|:----------------------------------------------|
| Info                                 | [alpha] [undocumented]                        |
| Variables                            | sambaName=$(/show/smbGetName),                |
| Modules                              | cp /do/samba/default/all /etc/samba/smb.conf, |
| 1. [SAMBA] share everything          |                                               |
| 1. [WARNING] This is highly unsecure |                                               |
| 2. \\\\$sambaName\sd --> SD card     |                                               |

| /opt/piget/samba/shareNothing   |                                                                                                                               |
|:--------------------------------|:------------------------------------------------------------------------------------------------------------------------------|
| Info                            | [alpha] [undocumented]                                                                                                        |
| Variables                       | isNeeded=$(grep -v -F -x -f /do/samba/default/name /etc/samba/smb.conf|wc -l), sambaName=$(/show/smbGetName),                 |
| Modules                         | isNeeded=$(grep -v -F -x -f /do/samba/default/name /etc/samba/smb.conf|wc -l), cp /do/samba/default/name /etc/samba/smb.conf, |
| 1. [SAMBA] - Share nothing      |                                                                                                                               |
| 1. Already done                 |                                                                                                                               |

| /opt/piget/samba/sharePiget         |                                                 |
|:------------------------------------|:------------------------------------------------|
| Info                                | [alpha] [undocumented]                          |
| Variables                           | sambaName=$(/show/smbGetName),                  |
| Modules                             | cp /do/samba/default/piget /etc/samba/smb.conf, |
| 1. [SAMBA] share Piget Folders      |                                                 |
| 1. \\\\$sambaName\piget --> Modules |                                                 |
| 2. \\\\$sambaName\user --> User     |                                                 |
| 3. \\\\$sambaName\boot --> SD card  |                                                 |

| /opt/piget/samba/shareUser   |                                                                     |
|:-----------------------------|:--------------------------------------------------------------------|
| Info                         | [alpha] [undocumented]                                              |
| Modules                      | cp -v /do/samba/default/user /etc/samba/smb.conf, /do/samba/secure, |

| /opt/piget/samba/shareWeb   |                                                  |
|:----------------------------|:-------------------------------------------------|
| Info                        | [alpha] [undocumented]                           |
| Modules                     | cp -v /do/samba/default/web /etc/samba/smb.conf, |

| /opt/piget/samba/start   |                        |
|:-------------------------|:-----------------------|
| Info                     | [alpha] [undocumented] |

| /opt/piget/samba/status   |                        |
|:--------------------------|:-----------------------|
| Info                      | [alpha] [undocumented] |

| /opt/piget/samba/stop   |                        |
|:------------------------|:-----------------------|
| Info                    | [alpha] [undocumented] |

| /opt/piget/samba/userConnected   |                                                     |
|:---------------------------------|:----------------------------------------------------|
| Info                             | [alpha] [undocumented]                              |
| Variables                        | status=$(smbstatus|grep "Locked files:"|tail -n 1), |

