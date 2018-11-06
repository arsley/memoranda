# Configuration

## Initial setting

```
# adduser assly
# usermod -aG sudo,docker assly
# cat /etc/group | grep assly
```

## SSH

1. `/etc/ssh/sshd_config` の修正
  - `PermitRootLogin no`
  - `PasswordAuthentication no`
  - `PubkeyAuthentication yes`
  - `Port xx`
2. 公開鍵認証設定
  - `mkdir ~/.ssh/ && chmod 700 ~/.ssh`
  - `curl -o ~/.ssh/authorized_keys https://github.com/username.keys`
  - `chmod 600 ~/.ssh/authorized_keys`
3. ポート変更(firewalld)
  - `cp /usr/lib/firewalld/services/ssh.xml /etc/firewalld/services`
  - `cp /etc/firewalled/services/ssh.xml /etc/firewalld/services/ssh.xml.old`
  - `port="xx"`
4. 適用
  - `systemctl restart sshd`
  - `firewall-cmd --reload`

## SSH (local config)

```
# ~/.ssh/config

Host labelOfHostname
  Hostname host.domain.here
  User user
  IdentityFile /your/private/rsa/key
  ServerAliveInterval 60 # To avoid refusing connection
  Port xx
```

```
$ ssh labelOfHostname
```


## Ref

- [SSH ポート番号変更](https://webkaru.net/linux/change-ssh-port/)
- [firewalld SSH ポート番号変更](https://webkaru.net/linux/centos7-firewalld-ssh-port/)
- [How To Set Up a Firewall Using FirewallD on CentOS 7 | DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-using-firewalld-on-centos-7)
- [How To Set Up a Firewall Using Iptables on Ubuntu 14.04 | DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-using-iptables-on-ubuntu-14-04)
- [43.9.4. Saving IPTables Rules](https://www.centos.org/docs/5/html/5.1/Deployment_Guide/s1-iptables-saving.html)
