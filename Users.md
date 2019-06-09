# Managing users on RHEL

First and foremost, adding users:
```
# adduser [new_user]
# useradd [new_user]
```
It is common practice in most Linux distros to use `useradd` in this regard.
By default when a new user account is added the following operations are performed:
- The home directory of the new user is created: `/home/username` (unless specified otherwise)
- Three dotfiles are made: `.bash_logout`, `.bash_profile`, `.bashrc`.
- A mail spool directory is created.
- A group is created with the same name as the new user.

The full account summary is stored in the `/etc/passwd` file. This holds a record per system and has this format:
```
[username]:[x]:[UID]:[GID]:[Comment]:[Home directory]:[Default shell]
```
- The `x` indicates the account is secured by shadowed password.
- The `[UID]` and `[GID]` fields shows the User Identification and the primary Group Indification.

Another file to remember is `/etc/group` where the group information is stored. It's record will be in this format:
```
[Group name]:[Group password]:[GID]:[Group members]
```
- If the group does not have a password this field will be marked with an X.
- `[GID]` is the same as in `/etc/passwd`.

# Editing with usermod
After creating an account these variables can be edited with:
```
# usermod [options] [username]
```
