## GitHub based key management ##

Uses https://github.com/yuvipanda/github-ssh-auth so I can always login with my github key!

# Put the file in `/usr/bin`, not `/usr/local/bin`, since sshd will paranoidly refuse to use it
# Make sure it is executable by nobody (permissions should be `0555`)
# Add the following to `/etc/ssh/sshd_config`:
  ```
  AuthorizedKeysCommand /usr/bin/github-keys-check.py
  AuthorizedKeysCommandUser nobody
  ```
# Create user account with same name as github account, and add to sudo if necessary. No passwords.
