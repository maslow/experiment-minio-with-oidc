
## intro

This experiment is to use casdoor as the OIDC IDP for minio. 

> replcae host conf with your host in `app.conf` and the following scripts.

## setup

```bash
docker-compose up
```

## casdoor config

1. create a new orgaization in casdoor, add `consoleAdmin` & `readwrite` tags to the orgaization.
2. create a new application in casdoor owned by the orgaization.
3. replace the `client_id` & `client_secret` in following scripts with the application's `id` & `secret`.
4. add `http://localhost:9001/oauth_callback` to the application's `redirect_uri` list.
5. create/signup a new user in casdoor, add `consoleAdmin` or `readwrite` tags to the user as its policy in minio.
6. run the following scripts to config minio oidc.

## scripts 

```bash

mc alias set oss http://localhost:9000 minio-root-user minio-root-password

mc admin config set oss identity_openid \
    config_url="http://192.168.3.7:8000/.well-known/openid-configuration" \
    client_id="c35559188a28f1d3ab12" \
    client_secret="e697f25063b099f6ad294a1644e387e80712e797" \
    claim_name="tag" \
    redirect_uri="http://localhost:9001/oauth_callback"

mc admin service restart oss
```

## references

- [casdoor with minio](https://casdoor.org/docs/integration/minio)
- [minio oidc](https://docs.min.io/minio/baremetal/security/openid-external-identity-management/configure-openid-external-identity-management.html)