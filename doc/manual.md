| /do/samba/addToStartup   |                              |
|:-------------------------|:-----------------------------|
| Description              | Samba will be start on boot  |
| Info                     | [beta] [service] [systemctl] |

| /do/samba/copy   |                                              |
|:-----------------|:---------------------------------------------|
| Description      | Copy a configuration to /etc/samba/smb.conf  |
| Example          | /do/samba/copy /user/settings/samba/smb.conf |
| Info             | [beta] [samba] [backup]                      |
| Arguments        | 1:settings,                                  |

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

| /do/samba/load   |                                                   |
|:-----------------|:--------------------------------------------------|
| Description      | Copy smb.conf from /user to current configuration |
| Example          | /do/samba/load                                    |
| Info             | [beta] [samba] [sync]                             |

| /do/samba/mount   |                                                                                                                                 |
|:------------------|:--------------------------------------------------------------------------------------------------------------------------------|
| Description       | Mount a samba share on your Raspberry Pi                                                                                        |
| Example           | /do/samba/mount \\\\madnerd\\piget /media/madnerd/piget or /do/samba/mount \\\\madnerd\\piget /media/madnerd/piget pi raspberry |
| Info              | [beta] [mount] [cifs]                                                                                                           |
| Arguments         | 1:local  ip, 1:uncpath, 2:dir, 1:uncpath, 2:dir, 3:user, 4:password,                                                            |

| /do/samba/password   |                                                                     |
|:---------------------|:--------------------------------------------------------------------|
| Description          | Change password for an user or by default pi                        |
| Example              | /do/samba/password badPassword or /do/samba/password pi badPassword |
| Info                 | [beta] [smbpasswd]                                                  |
| Arguments            | 1:username, 2:password, 1:password,                                 |

| /do/samba/removeFromStartup   |                              |
|:------------------------------|:-----------------------------|
| Description                   | Samba will not start at boot |
| Info                          | [beta] [service] [systemctl] |

| /do/samba/restart   |                             |
|:--------------------|:----------------------------|
| Description         | Restart samba services      |
| Info                | [release] [samba] [service] |

| /do/samba/save   |                                              |
|:-----------------|:---------------------------------------------|
| Description      | Save current configuration to /user/settings |
| Info             | [beta] [samba] [backup]                      |

| /do/samba/settings   |                                             |
|:---------------------|:--------------------------------------------|
| Description          | Modify /etc/samba/smb.conf with nano editor |
| Info                 | [beta] [samba] [interactive]                |

| /do/samba/setupPassword   |                                                                           |
|:--------------------------|:--------------------------------------------------------------------------|
| Description               | Change password for an user or by default pi (interactive)                |
| Example                   | /do/samba/setupPassword raspberry or /do/samba/setupPassword pi raspberry |
| Info                      | [beta] [smbpasswd] [interactive]                                          |
| Arguments                 | 1:username,                                                               |

| /do/samba/shareAll   |                                               |
|:---------------------|:----------------------------------------------|
| Description          | Share the entire SDcard (use it with caution) |
| Example              | /do/samba/shareAll                            |
| Info                 | [beta] [samba] [danger] [share]               |

| /do/samba/shareNothing   |                                                                                   |
|:-------------------------|:----------------------------------------------------------------------------------|
| Description              | Share nothing but keep netbios name (will do nothing if this is already the case) |
| Example                  | /do/samba/shareNothing                                                            |
| Info                     | [beta] [samba] [share]                                                            |

| /do/samba/sharePiget   |                                            |
|:-----------------------|:-------------------------------------------|
| Description            | Share /opt/piget /opt/user and /boot/piget |
| Example                | /do/samba/sharePiget                       |
| Info                   | [beta] [samba] [share]                     |

| /do/samba/shareUser   |                               |
|:----------------------|:------------------------------|
| Description           | Share /opt/user (user folder) |
| Example               | /do/samba/shareUser           |
| Info                  | [beta] [samba] [share]        |

| /do/samba/shareWeb   |                                         |
|:---------------------|:----------------------------------------|
| Description          | Share /var/www (using www-data as user) |
| Example              | /do/samba/shareWeb                      |
| Info                 | [beta] [samba] [share]                  |

| /do/samba/start   |                            |
|:------------------|:---------------------------|
| Description       | Start samba services       |
| Info              | [release] [samba] [init.d] |

| /do/samba/status   |                               |
|:-------------------|:------------------------------|
| Description        | Display status of samba share |
| Info               | [release] [samba] [smbstatus] |

| /do/samba/stop   |                            |
|:-----------------|:---------------------------|
| Description      | Stop samba services        |
| Info             | [release] [samba] [init.d] |

| /do/samba/unmount   |                             |
|:--------------------|:----------------------------|
| Description         | Unmount a samba share       |
| Example             | /do/samba/unmount directory |
| Info                | [beta] [umount]             |
| Arguments           | 1:dir,                      |

| /do/samba/userConnected   |                                               |
|:--------------------------|:----------------------------------------------|
| Description               | Show if a user is connected to samba share    |
| Info                      | [beta] [samba] [smbstatus] [boolean] [return] |

