# DNS records

## About

- DNSレコードの情報が書かれた*ゾーンファイル(Zone file)*なるものがある
- DNSは普通2台同時に稼働している
  - Primary, Secondary
- DNSは2種類ある
  - Cache server
  - Contents server

## SOA

```
[Domain name] [class name] SOA [DNS server's domain name] [Contact] [Serial] [Refresh] [Retry] [Expire] [Minimum]
```

- `[DNS server's domain name]` = `MNAME`
  - ゾーンファイルの参照先NS(の名前)
  - プライマリのNS
- `[Contact]` = `RNAME`
  - このドメインの管理者
- `[Serial]`
  - ゾーンファイルのバージョンのようなもの
  - この値を確認してPrimary → Secondaryへのゾーンファイル更新可否
- `[Refresh]`
  - Secondaryによるゾーンファイルの更新確認間隔
- `[Retry]`
  - `[Refresh]` 失敗時の再実行までの待ち時間
- `[Expire]`
  - ゾーンファイル更新を諦めるまでの時間
  - Secondaryの保持する情報を利用していい期間
- `[Minimum]`
  - ネガティブキャッシュの保持時間

```zone_file.example
@ IN SOA ns1.example.jp. who.example.jp. (
  2003081901 　; Serial
  3600 ; Refresh　
  900  ; Retry
  604800 ; Expire
  3600   ; Negative cache TTL
  )
  ; This is a comment
```

### Standard

- `[Domain name]` は `@`
- `[class name]` は大抵 `IN` (*In*ternet の略)


## Ref

- [SOAレコードには...](http://www.atmarkit.co.jp/fnetwork/dnstips/014.html)
- [Zone file](https://wa3.i-3-i.info/word12283.html)
- [SOAレコードとは...](https://wa3.i-3-i.info/word12285.html)
