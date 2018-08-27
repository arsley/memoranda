# Solve

## Errno::EACCES (Permission denied @ dir_s_mkdir - /mastodon/public/system/accounts):

Run above.

```
docker-compose run --rm -u root web chown -R mastodon:mastodon public/
```

