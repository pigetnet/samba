| /opt/piget/samba/addToStartup   |                              |
|:--------------------------------|:-----------------------------|
| Description                     | Samba will be start on boot  |
| Info                            | [beta] [service] [systemctl] |

| /opt/piget/samba/copy   |                                               |
|:------------------------|:----------------------------------------------|
| Description             | Copy a configuration to /etc/samba/smb.conf   |
| Example                 | /opt/piget/samba/copy /user/config/samba.conf |
| Info                    | [beta] [samba] [backup]                       |
| Arguments               | 1:settings,                                   |

| /opt/piget/samba/download   |                                    |
|:----------------------------|:-----------------------------------|
| Description                 | Download a configuration on github |
| Info                        | [beta] [wget] [github] [backup]    |
| Arguments                   | 1:repo, 2:sambaconf,               |

| /opt/piget/samba/install   |                                                                         |
|:---------------------------|:------------------------------------------------------------------------|
| Description                | Install samba and samba tools and set a default password (pi:raspberry) |
| Info                       | [beta] [samba] [install]                                                |

| /opt/piget/samba/isNameOnly   |                                 |
|:------------------------------|:--------------------------------|
| Description                   | Check if samba shares something |
| Info                          | [beta] [samba] [variable]       |

| /opt/piget/samba/listUsers   |                                 |
|:-----------------------------|:--------------------------------|
| Description                  | Display samba users             |
| Info                         | [beta] [samba] [list] [pdbedit] |

| /opt/piget/samba/load   |                                                   |
|:------------------------|:--------------------------------------------------|
| Description             | Copy smb.conf from /user to current configuration |
| Example                 | /opt/piget/samba/load                             |
| Info                    | [beta] [samba] [sync]                             |

| /opt/piget/samba/mount   |                                                                                                                                               |
|:-------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------|
| Description              | Mount a samba share on your Raspberry Pi                                                                                                      |
| Example                  | /opt/piget/samba/mount \\\\madnerd\\piget /media/madnerd/piget or /opt/piget/samba/mount \\\\madnerd\\piget /media/madnerd/piget pi raspberry |
| Info                     | [beta] [mount] [cifs]                                                                                                                         |
| Arguments                | 1:local  ip, 1:uncpath, 2:dir, 1:uncpath, 2:dir, 3:user, 4:password,                                                                          |

| /opt/piget/samba/password   |                                                                                   |
|:----------------------------|:----------------------------------------------------------------------------------|
| Description                 | Change password for an user or by default pi                                      |
| Example                     | /opt/piget/samba/password badPassword or /opt/piget/samba/password pi badPassword |
| Info                        | [beta] [smbpasswd]                                                                |
| Arguments                   | 1:username, 2:password, 1:password,                                               |

| /opt/piget/samba/removeFromStartup   |                              |
|:-------------------------------------|:-----------------------------|
| Description                          | Samba will not start at boot |
| Info                                 | [beta] [service] [systemctl] |

| /opt/piget/samba/restart   |                             |
|:---------------------------|:----------------------------|
| Description                | Restart samba services      |
| Info                       | [release] [samba] [service] |

| /opt/piget/samba/save   |                                               |
|:------------------------|:----------------------------------------------|
| Description             | Save current configuration to /boot and /user |
| Info                    | [beta] [samba] [backup]                       |

| /opt/piget/samba/settings   |                                             |
|:----------------------------|:--------------------------------------------|
| Description                 | Modify /etc/samba/smb.conf with nano editor |
| Info                        | [beta] [samba] [interactive]                |

| /opt/piget/samba/setupPassword   |                                                                                         |
|:---------------------------------|:----------------------------------------------------------------------------------------|
| Description                      | Change password for an user or by default pi (interactive)                              |
| Example                          | /opt/piget/samba/setupPassword raspberry or /opt/piget/samba/setupPassword pi raspberry |
| Info                             | [beta] [smbpasswd] [interactive]                                                        |
| Arguments                        | 1:username,                                                                             |

| /opt/piget/samba/shareAll   |                                               |
|:----------------------------|:----------------------------------------------|
| Description                 | Share the entire SDcard (use it with caution) |
| Example                     | /opt/piget/samba/shareAll                     |
| Info                        | [beta] [samba] [danger] [share]               |

| /opt/piget/samba/shareNothing   |                                                                                   |
|:--------------------------------|:----------------------------------------------------------------------------------|
| Description                     | Share nothing but keep netbios name (will do nothing if this is already the case) |
| Example                         | /opt/piget/samba/shareNothing                                                     |
| Info                            | [beta] [samba] [share]                                                            |

| /opt/piget/samba/sharePiget   |                                            |
|:------------------------------|:-------------------------------------------|
| Description                   | Share /opt/piget /opt/user and /boot/piget |
| Example                       | /opt/piget/samba/sharePiget                |
| Info                          | [beta] [samba] [share]                     |

| /opt/piget/samba/shareUser   |                               |
|:-----------------------------|:------------------------------|
| Description                  | Share /opt/user (user folder) |
| Example                      | /opt/piget/samba/shareUser    |
| Info                         | [beta] [samba] [share]        |

| /opt/piget/samba/shareWeb   |                                         |
|:----------------------------|:----------------------------------------|
| Description                 | Share /var/www (using www-data as user) |
| Example                     | /opt/piget/samba/shareWeb               |
| Info                        | [beta] [samba] [share]                  |

| /opt/piget/samba/start   |                            |
|:-------------------------|:---------------------------|
| Description              | Start samba services       |
| Info                     | [release] [samba] [init.d] |

| /opt/piget/samba/status   |                               |
|:--------------------------|:------------------------------|
| Description               | Display status of samba share |
| Info                      | [release] [samba] [smbstatus] |

| /opt/piget/samba/stop   |                            |
|:------------------------|:---------------------------|
| Description             | Stop samba services        |
| Info                    | [release] [samba] [init.d] |

| /opt/piget/samba/unmount   |                                    |
|:---------------------------|:-----------------------------------|
| Description                | Unmount a samba share              |
| Example                    | /opt/piget/samba/unmount directory |
| Info                       | [beta] [umount]                    |
| Arguments                  | 1:dir,                             |

| /opt/piget/samba/userConnected   |                                               |
|:---------------------------------|:----------------------------------------------|
| Description                      | Show if a user is connected to samba share    |
| Info                             | [beta] [samba] [smbstatus] [boolean] [return] |

