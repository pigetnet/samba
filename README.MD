# piget-samba
Install Windows File Sharing (smb)    
Windows network shares are compatible with all operating systems.     
You can access shared folders in Network on Windows explorer       

![Logo](https://raw.githubusercontent.com/pigetnet/samba/master/doc/piget-samba.png)

# Install

````
/pi/install samba
````

# Change Password
```
/do/samba/password
```


# Shares files
User : pi    
 
Shares scripts/user files (/do/ /user/)
```
/do/samba/sharePiget
```

# Change names
If you want to change the name of your Raspberry Pi, type 
```
/pi/setup
```

# Fix issues on Windows
If you have previously entered a different password, this may have been cached by Windows, we can’t change it and an error message will be displayed.

![error](https://github.com/pigetnet/samba/raw/dev/doc/error.png)

There are 3 ways to fix this:

* close and open your session
* restart your computer
* Type these commands on the command line as an Administrator (Shortcut : WINDOWS-X then A)
```
net stop workstation
net start workstation
```
