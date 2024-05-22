# SSH Howto

## keys

Create keys
```
ssh-keygen -t rsa -b 4096 -N '' -C "me@example.com" -f ~/.ssh/id_rsa
```

Set file permssions
```
chmod 700 ~/.ssh
chmod 644 ~/.ssh/authorized_keys
chmod 644 ~/.ssh/known_hosts
chmod 644 ~/.ssh/config
chmod 600 ~/.ssh/id_rsa
chmod 644 ~/.ssh/id_rsa.pub
```

[Correct file permssions](https://gist.github.com/denisgolius/d846af3ad5ce661dbca0335ec35e3d39)

## Use keys

on the target host add the pub key to '~/.ssh/authirized_keys'

```
 ssh -i <priv_id> <usr>@<host>
```


## Use __old__ algorithms

add missing algorithm ssh  

edit file /etc/ssh/ssh_config
```
Host *
# ....
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
```
missing algorithms to use old keys:
```
    HostKeyAlgorithms +ssh-rsa,ssh-dss
    KexAlgorithms +diffie-hellman-group1-sha1
    PubkeyAcceptedAlgorithms +ssh-rsa
```

Find:

git permission denied
ssh permission denied
ssh old modules
ssh old algorithms
ssh add modules
ssh add algorithms
