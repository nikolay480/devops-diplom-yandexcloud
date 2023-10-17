
https://cloud.yandex.ru/docs/container-registry/operations/authentication#sa

# Аутентификация с помощью OAuth-токена
`$ docker login --username oauth --password `
# Аутентификация с помощью json_key service account
```bash
$ cat key.json | docker login \
  --username json_key \
  --password-stdin \
  cr.yandex
WARNING! Your password will be stored unencrypted in /home/nik/.docker/config.json.
Configure a credential helper to remove this warning. See
https://docs.docker.com/engine/reference/commandline/login/#credentials-store

Login Succeeded
```
