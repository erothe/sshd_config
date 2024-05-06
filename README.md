# sshd_config
This is the `sshd_config` configuration I use for my home server.

I intend to update this file whenever I found a new security best practice.
Feel free to open a pull request if you think that it would be cool to 
contribute to my home server security.

## Configuration
```bash
# Sets the port number to something
# different from the standard 22 port
Port some-random-integer

# Forbids root login
PermitRootLogin no

# I want to forbid everyone and only allow my user,
# but I haven't yet figured out how to do this.
# I thought that having the AllowUsers keyword after
# the DenyUsers would let me do the trick, but it does not.
#
# DenyUsers *
# AllowUsers user
#
# So, while I haven't figure a way to do this, I just leave
# the keyword here (commented) as a reminder to come back
# some time later in the future.

# DenyUsers *
AllowUsers user1 user2 user3

# Restrict authentication methods to Public Key
# Authentication.
PubkeyAuthentication yes
PasswordAuthentication no

# Disable attempting connections using other
# protocols than version 2
Protocol 2
```

## Caveats

* I use a non standard port number for service `ssh` (keyword: `Port`) and I
  only allow a small number of users to access remotely the server (keyword: `AllowUsers`). For security reasons, I do not publish my personal data. 

* You can use variants of the bellow command to validate that `sshd` is reading
  the configuration as expected.

```bash
sshd -T |egrep '^port|^allowu|^permitr'
```
