| /do/samba/addToStartup   |                              |
|:-------------------------|:-----------------------------|
| Description              | Samba will be start on boot  |
| Info                     | [beta] [service] [systemctl] |

| /do/samba/copy   |                                             |
|:-----------------|:--------------------------------------------|
| Description      | Copy a configuration to /etc/samba/smb.conf |
| Example          | /do/samba/copy /user/config/samba.conf      |
| Info             | [beta] [samba] [backup]                     |
| Arguments        | 1:settings,                                 |

| /do/samba/download   |                                    |
|:---------------------|:-----------------------------------|
| Description          | Download a configuration on github |
| Info                 | [beta] [wget] [github] [backup]    |
| Arguments            | 1:repo, 2:sambaconf,               |

| /do/samba/install   |                                                                         |
|:--------------------|:------------------------------------------------------------------------|
| Description         | Install samba and samba tools and set a default password (pi:raspberry) |
| Info                | [beta] [samba] [install]                                                |

| /do/samba/isNameOnly   |                                 |
|:-----------------------|:--------------------------------|
| Description            | Check if samba shares something |
| Info                   | [beta] [samba] [variable]       |

| /do/samba/listUsers   |                                 |
|:----------------------|:--------------------------------|
| Description           | Display samba users             |
| Info                  | [beta] [samba] [list] [pdbedit] |

| /do/samba/load   |                        |
|:-----------------|:-----------------------|
| Info             | [alpha] [undocumented] |

| /do/samba/mount   |                        |
|:------------------|:-----------------------|
| Info              | [alpha] [undocumented] |
| Arguments         | 1:uncpath, 2:dir,      |

| /do/samba/password   |                                                                     |
|:---------------------|:--------------------------------------------------------------------|
| Description          | Change password for an user or by default pi                        |
| Example              | /do/samba/password badPassword or /do/samba/password pi badPassword |
| Info                 | [beta] [smbpasswd]                                                  |
| Arguments            | 1:username, 2:password, 1:password,                                 |

| /do/samba/public   |                        |
|:-------------------|:-----------------------|
| Info               | [alpha] [undocumented] |

| /do/samba/remove   |                        |
|:-------------------|:-----------------------|
| Info               | [alpha] [undocumented] |

| /do/samba/removeFromStartup   |                              |
|:------------------------------|:-----------------------------|
| Description                   | Samba will be start on boot  |
| Info                          | [beta] [service] [systemctl] |

| /do/samba/rename   |                         |
|:-------------------|:------------------------|
| Example            | sambaRename raspberrypi |
| Info               | [alpha] [undocumented]  |
| Arguments          | 1:NEW_HOSTNAME,         |

| /do/samba/restart   |                        |
|:--------------------|:-----------------------|
| Info                | [alpha] [undocumented] |

| /do/samba/save   |                                               |
|:-----------------|:----------------------------------------------|
| Description      | Save current configuration to /boot and /user |
| Example          | /do/samba/save                                |
| Info             | [beta] [samba] [backup]                       |

| /do/samba/secure   |                        |
|:-------------------|:-----------------------|
| Info               | [alpha] [undocumented] |

| /do/samba/settings   |                        |
|:---------------------|:-----------------------|
| Info                 | [alpha] [undocumented] |

| /do/samba/setupPassword   |                                                                           |
|:--------------------------|:--------------------------------------------------------------------------|
| Description               | Change password for an user or by default pi (interactive)                |
| Example                   | /do/samba/setupPassword raspberry or /do/samba/setupPassword pi raspberry |
| Info                      | [beta] [smbpasswd] [interactive]                                          |
| Arguments                 | 1:username,                                                               |

| /do/samba/shareAll   |                        |
|:---------------------|:-----------------------|
| Info                 | [alpha] [undocumented] |

| /do/samba/shareNothing   |                        |
|:-------------------------|:-----------------------|
| Info                     | [alpha] [undocumented] |

| /do/samba/sharePiget   |                        |
|:-----------------------|:-----------------------|
| Info                   | [alpha] [undocumented] |

| /do/samba/shareUser   |                        |
|:----------------------|:-----------------------|
| Info                  | [alpha] [undocumented] |

| /do/samba/shareWeb   |                        |
|:---------------------|:-----------------------|
| Info                 | [alpha] [undocumented] |

| /do/samba/start   |                             |
|:------------------|:----------------------------|
| Description       | Start samba services        |
| Info              | [release] [samba] [service] |

| /do/samba/status   |                               |
|:-------------------|:------------------------------|
| Description        | Display status of samba share |
| Info               | [release] [samba] [smbstatus] |

| /do/samba/stop   |                             |
|:-----------------|:----------------------------|
| Description      | Stop samba services         |
| Info             | [release] [samba] [service] |

| /do/samba/userConnected   |                                               |
|:--------------------------|:----------------------------------------------|
| Description               | Show if a user is connected to samba share    |
| Info                      | [beta] [samba] [smbstatus] [boolean] [return] |

