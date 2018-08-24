# Practice

## 1

下記のURLにアクセスして、それ自身のテキストを返すサーバーを構築する。

- `foo.kstm.tld`
- `bar.kstm.tld`

確認には次のコマンドを用いる。

```testing
curl -s foo.kstm.tld -H 'Host: foo.kstm.tld' | grep foo.kstm.tld
curl -s bar.kstm.tld -H 'Host: bar.kstm.tld' | grep bar.kstm.tld
```

### Ans

Nginxでの解法。

```nginx.conf
# 略

server {
  listen 80;
  listen [::]:80; # IPv6
  server_name foo.kstm.tld;

  location / {
    return 200 "foo.kstm.tld\n";
  }
}

server {
  listen 80;
  listen [::]:80; # IPv6
  server_name bar.kstm.tld;

  location / {
    return 200 "bar.kstm.tld\n";
  }
}
```

```/etc/hosts
127.0.0.1 foo.kstm.tld
127.0.0.1 bar.kstm.tld
```
