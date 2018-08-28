# Configuration

## Initial setting

1. 新規ユーザ作成 `useradd`
2. `visudo` による `sudo` 実行権限付与

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
