

## scripts 

```bash

mc alias set minio http://localhost:9000 minio-root-user minio-root-password

mc admin config set minio identity_openid config_url="http://localhost:8000/.well-known/openid-configuration" client_id="904adb32b9023be79305" client_secret="f46690a538fae90ca8e4261a71e860049b3c1f4c" claim_name="tag"

```