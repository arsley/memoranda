# Install Phusion Passenger to nginx

## Prerequisites

```
$ sudo yum install -y epel-release
```

## Main

```
$ sudo curl --fail -sSLo /etc/yum.repos.d/passenger.repo https://oss-binaries.phusionpassenger.com/yum/definitions/el-passenger.repo
$ sudo yum install -y nginx passenger || sudo yum-config-manager --enable cr && sudo yum install -y nginx passenger
```

This generates `/etc/nginx/conf.d/passenger.conf`:

```
# passenger_root /some-filename/locations.ini;
# passenger_ruby /usr/bin/ruby;
# passenger_instance_registry_dir /var/run/passenger-instreg;
```

Replace `passenger_root`'s path to:

```
$ passenger-config --root
```

Replace `passenger_ruby`'s path to:

```
$ passenger-config about ruby-command
#=> To use in Nginx: passenger_ruby /path/to/your/ruby's/bin
```

Comment in `passenger_instance_registry_dir`.

### Conf(sample)

```
# /etc/nginx/conf.d/yourapp.conf

server {
  listen 80;
  server_name hogehoge.work;

  root /path/to/your/app's/public/dir;

  passenger_enabled on;
  passenger_user USERNAME;
  passenger_app_env development;


  client_max_body_size 100m;

  location ^~ /assets/ {
    access_log off;
    gzip_static on;
    expires 0;
    add_header Cache-Control public;
    add_header ETag "";
    add_header Access-Control-Allow-Origin *;
    add_header Access-Control-Request-Method *;
  }
}
```

### Restart

```
$ nginx -t
$ systemctl restart nginx
```
