## GitHub based key management ##

Uses https://github.com/yuvipanda/github-ssh-auth so I can always login with my github key!

1. Put the file in `/usr/bin`, not `/usr/local/bin`, since sshd will paranoidly refuse to use it
2. Make sure it is executable by nobody (permissions should be `0555`)
3. Add the following to `/etc/ssh/sshd_config`:
  ```
  AuthorizedKeysCommand /usr/bin/github-keys-check.py
  AuthorizedKeysCommandUser nobody
  ```
4. Create user account with same name as github account. No passwords. You can do this by:
   ```
   adduser --disabled-password  yuvipanda
   ```
5. Allow users in sudo group to sudo without passwords. You can do this by editing this line:
   ```
   %sudo   ALL=(ALL:ALL)  ALL
   ```
   in `/etc/sudoers` to be:
  ```
   %sudo   ALL=(ALL:ALL) NOPASSWD: ALL
  ```
