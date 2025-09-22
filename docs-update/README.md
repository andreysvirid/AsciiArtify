# AsciiArtify

AsciiArtify — це демонстраційний проєкт, який розробляється етапами (Concept → POC → MVP), 
щоб показати повний життєвий цикл створення продукту з практикою GitOps (Flux / ArgoCD).

## 📑 Документація
- [Concept](doc/Concept.md)  
- [POC](doc/POC.md)  
- [MVP](doc/MVP.md)  

## 🚀 MVP Demo
- **ArgoCD автоматично синхронізує застосунок** з GitHub-репозиторію:  
  https://github.com/den-vasyliev/go-demo-app  
- **Відео-демо синхронізації:** [посилання на YouTube]  
- **Демо роботи застосунку:**  
  ```bash
  kubectl port-forward svc/go-demo-app 8080:80
  curl http://localhost:8080
Очікуваний результат: сторінка / відповідь від go-demo-app

---

## 📝 Файл `doc/MVP.md`

```markdown
# AsciiArtify MVP

## 🎯 Мета
Розгорнути застосунок `go-demo-app` у Kubernetes з використанням ArgoCD, 
налаштувати автоматичну синхронізацію та продемонструвати роботу MVP.

## ⚙️ Інфраструктура
- Kubernetes кластер (Minikube)
- ArgoCD (namespace `argocd`)
- GitOps підхід: зміни у Git автоматично застосовуються у кластері

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
Синхронізація: [посилання на відео / gif]

Робота застосунку:

kubectl port-forward svc/go-demo-app 8080:80
curl http://localhost:8080

Очікувана відповідь: робочий HTML/API від go-demo-app

✅ Результат

MVP запущено в Kubernetes.

ArgoCD забезпечує автоматичну доставку.

Застосунок доступний для користувачів.
