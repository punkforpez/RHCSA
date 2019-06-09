# Registering a RHEL 7/8 System with Red Hat Network.
This will have to be completed within thirty days on a test system but can be completed right away either on first boot or by issuing a series of commands.

Without registration, RHEL is considered "unsupported" and will not receive updates or be able to use any of the Red Hat repos. DNF/Yum will not work, even for simple package installation.

## As Root or on first boot (Root)
```
# subscription-manager register
```

The system will prompt for Username/Password from Red Hat (Red Hat Developer Site)
```
# subscription-manager auto-attach
```

Generally this is all that is needed, but attempt an update first and if that fails you might have to run:
```
# subscription-manager clean
```
This should pop-up a GUI manager for registering with Red Hat (if it hasn't already) and after going through the similar steps on that setup you should be able to update the system.

```
# yum update
```
