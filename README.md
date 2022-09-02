

## scripts 

```bash

mc alias set oss http://localhost:9000 minio-root-user minio-root-password

mc admin config set oss identity_openid config_url="http://localhost:8000/.well-known/openid-configuration" client_id="c35559188a28f1d3ab12" client_secret="e697f25063b099f6ad294a1644e387e80712e797" claim_name="tag"

mc admin service restart oss
```