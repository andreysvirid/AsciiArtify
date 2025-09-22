# Proof of Concept (PoC)

## 🎯 Ціль
Запустити мінімальний робочий моніторинговий стек і розгорнути тестовий застосунок.

## ⚙️ Інфраструктура
- Kubernetes кластер (Minikube)
- Prometheus + Grafana
- Loki + Promtail
- OpenTelemetry Collector

## 🚀 Розгортання
```bash
kubectl apply -f manifests/ -R
kubectl get pods -n default
📊 Демо
Grafana доступна через:

bash
Копировать код
kubectl port-forward svc/grafana 3000:3000
Далі відкрий http://localhost:3000

Імпортовано дашборд із CPU/Memory метриками та логами.

✅ Результат
Моніторинг і логування працюють у локальному середовищі.