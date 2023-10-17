

Сначала добавим  prometheus-community репозиторий.

`helm repo add prometheus-community https://prometheus-community.github.io/helm-charts`


Затем обновим его:

`helm repo update`

Cоздадим неймспейс:

`kubectl create namespace monitoring`

и установим  `kube-prometheus`:

`helm install kube-prom-stack prometheus-community/kube-prometheus-stack -n monitoring -f values.yml`
