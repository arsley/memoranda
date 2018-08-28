# Solution

## CSS Cache

```
# /etc/nginx/nginx.conf

http {
  proxy_cache_path /var/cache/nginx keys_zone=zone1:1m max_size=1g inactive=24h;
  proxy_temp_path  /var/cache/nginx_tmp;

  ...

  server {
    ...

    location / {
      proxy_cache zone1;
      add_header X-Nginx-Cache $upstream_cache_status;
    }

    location /css/ {
      alias /home/ishocon/webapp/ruby/public/css/;
    }
...
```

- [Ref](https://qiita.com/aosho235/items/bb1276a8c43e41edfc6f)
- [Ref2](https://qiita.com/MahoTakara/items/cbd97794828b30d9a4b3)

## Improve /vote

```
# app.rb

...

get '/vote/ do
  # candidates = db.query('SELECT * FROM candidates')
  candidates = db.query('SELECT name FROM candidates')
  ...
end

post '/vote' do
  ...
  # candidates = db.query('SELECT * FROM candidates')
  candidates = db.query('SELECT name FROM candidates')
  ...
end
```

## Add Index

```
mysql> ALTER TABLE candidates ADD INDEX (id, political_party);
mysql> ALTER TABLE votes ADD INDEX (user_id, candidate_id);
```

- [Ref3](http://blog.nomadscafe.jp/2014/08/isucon-web-apps-tune.html)

## Result

on Docker ... 2072 ...
