```sh
# Create the client
docker compose run --rm hydra create oauth2-client \
    --endpoint http://hydra:4445/ \
    --name svelte2-app \
    --grant-type authorization_code,refresh_token \
    --response-type code,id_token \
    --scope openid,email,profile \
    --redirect-uri http://localhost:4455/api/auth/callback/kratos-hydra
```

```sh
# from https://www.ory.sh/docs/hydra/self-hosted/configure-deploy#perform-oauth-20-flow
docker run --rm -it \
  -e HYDRA_ADMIN_URL=https://ory-hydra-example--hydra:4445 \
  --network hydraguide \
  oryd/hydra:v1.10.6 \
  clients create --skip-tls-verify \
    --id facebook-photo-backup \
    --secret some-secret \
    --grant-types authorization_code,refresh_token,client_credentials,implicit \
    --response-types token,code,id_token \
    --scope openid,offline,photos.read \
    --callbacks http://127.0.0.1:9010/callback
```
