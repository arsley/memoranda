# Alpine + rc-service + unbound

## Dockerfile

```
FROM alpine:3.8

RUN echo '@edge http://dl-cdn.alpinelinux.org/alpine/edge/main' >> /etc/apk/repositories \
    && echo '@edgecommunity http://dl-cdn.alpinelinux.org/alpine/edge/community' >> /etc/apk/repositories \
    && echo '@testing http://dl-cdn.alpinelinux.org/alpine/edge/testing' >> /etc/apk/repositories \
    && apk add --no-cache openrc su-exec ca-certificates nano curl findutils \
    # Disable getty's
    && sed -i 's/^\(tty\d\:\:\)/#\1/g' /etc/inittab \
    && sed -i \
        # Change subsystem type to "docker"
        -e 's/#rc_sys=".*"/rc_sys="docker"/g' \
        # Allow all variables through
        -e 's/#rc_env_allow=".*"/rc_env_allow="\*"/g' \
        # Start crashed services
        -e 's/#rc_crashed_stop=.*/rc_crashed_stop=NO/g' \
        -e 's/#rc_crashed_start=.*/rc_crashed_start=YES/g' \
        # Define extra dependencies for services
        -e 's/#rc_provide=".*"/rc_provide="loopback net"/g' \
        /etc/rc.conf \
    # Remove unnecessary services
    && rm -f /etc/init.d/hwdrivers \
            /etc/init.d/hwclock \
            /etc/init.d/hwdrivers \
            /etc/init.d/modules \
            /etc/init.d/modules-load \
            /etc/init.d/modloop \
    # Can't do cgroups
    && sed -i 's/\tcgroup_add_service/\t#cgroup_add_service/g' /lib/rc/sh/openrc-run.sh \
    && sed -i 's/VSERVER/DOCKER/Ig' /lib/rc/sh/init.sh

WORKDIR /etc/init.d
CMD ["/sbin/init"]
```

ref: [3.8-openrc](https://github.com/dockage/alpine/blob/master/3.8/openrc/Dockerfile)

## Ref

- [Unbound with Docker](https://qiita.com/flny/items/c0fd01db5fb3de6f8098)
- [Unbound @IT](http://www.atmarkit.co.jp/flinux/special/unbound/unboundb.html)
- [Alpine service](https://www.cyberciti.biz/faq/how-to-enable-and-start-services-on-alpine-linux/)
- [Setting up unbound DNS server](https://wiki.alpinelinux.org/wiki/Setting_up_unbound_DNS_server)
