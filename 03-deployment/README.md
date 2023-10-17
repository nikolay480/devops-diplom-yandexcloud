Перед запуском установим в кластер `secret` для доступ к YC Registry согласно [Документации](https://cloud.yandex.ru/docs/container-registry/operations/authentication#method).

1. Получим и сохраним в файл key.json авторизованный ключ для сервисного аккаунта `sa`:
```
yc iam key create --service-account-name sa -o key.json
```

2. Выполним команду аутентификации:

```
cat key.json | docker login \
  --username json_key \
  --password-stdin \
  cr.yandex
```
3. Убедимся, что полученный ключ имеет нужный формат. Для этого откроем конфигурационный файл Docker:

```
cat $HOME/.docker/config.json
```
4. Создадим секрет:
   
```   
   kubectl create secret generic cr-key-json \
  --namespace=gitlab \
  --from-file=.dockerconfigjson=$HOME/.docker/config.json \
  --type=kubernetes.io/dockerconfigjson
```

В манифесте deployment необходимо указать:

```
imagePullSecrets:
 - name: cr-key-secret
```

Далее применим манифест k8s.yaml.