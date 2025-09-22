```markdown
# MVP

## 🎯 Ціль
Розгорнути застосунок `go-demo-app` у Kubernetes з використанням ArgoCD, 
налаштувати автоматичну синхронізацію та продемонструвати роботу MVP.

## ⚙️ Інфраструктура
- Kubernetes кластер (Minikube)
- ArgoCD (namespace `argocd`)
- GitOps: зміни у Git автоматично застосовуються у кластері

## 🚀 ArgoCD Application

```yaml
apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: go-demo-app
  namespace: argocd
spec:
  project: default
  source:
    repoURL: https://github.com/den-vasyliev/go-demo-app
    targetRevision: main
    path: k8s
  destination:
    server: https://kubernetes.default.svc
    namespace: default
  syncPolicy:
    automated:
      prune: true
      selfHeal: true
🔄 Потік розгортання
Розробник робить commit у main гілку go-demo-app.

ArgoCD автоматично підтягує зміни.

Кластер синхронізується без ручного втручання.

Застосунок оновлюється у Kubernetes.

📹 Демо
Синхронізація: ArgoCD Application у стані Synced / Healthy

Робота застосунку:

bash
Копировать код
kubectl port-forward svc/go-demo-app 8080:80
curl http://localhost:8080
Очікувана відповідь: робочий HTML/API від go-demo-app

✅ Результат
MVP запущено в Kubernetes.

ArgoCD забезпечує автоматичну доставку.

Застосунок доступний і функціонує у кластері.
