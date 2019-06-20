# Systemd Runlevels

## Table of Runlevels (SysV / Systemd)
```
Runlevel	Target Units		Description
0		runlevel0.target	Shutdown / Power-off
		poweroff.target

1		runlevel1.target	Set up a rescue shell
		rescue.target

2		runlevel2.target	Set up a non-graphical user system
		multi-user.target

3		runlevel3.target	Same as Runlevel 2
		multi-user.target

4		runlevel4.target	Same as 2 & 3
		multi-user.target

5		runlevel5.target	Set up a graphical user system
		graphical.target

6		runlevel6.target	Shut down and reboot
		reboot.target
```

**Note**

Running the system at Runlevels 2-4 will still result in a fully working, bootable system with multiple user logons permitted but will start up the system at a TTY and not the normal graphical manager (GDM, etc).


