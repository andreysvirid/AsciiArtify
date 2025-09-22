# AsciiArtify

AsciiArtify — демонстраційний проєкт, що показує повний цикл створення продукту з DevOps практиками GitOps.

Проєкт проходить кілька етапів:
- [Concept](doc/Concept.md)
- [POC](doc/POC.md)
- [MVP](doc/MVP.md)

## 🚀 MVP Demo

- **ArgoCD автоматично синхронізує застосунок** з GitHub-репозиторію:  
  https://github.com/den-vasyliev/go-demo-app  

- **Демо роботи застосунку:**  
  ```bash
  kubectl port-forward svc/go-demo-app 8080:80
  curl http://localhost:8080
Очікуваний результат: сторінка або API-відповідь від go-demo-app

Демо синхронізації: зміни у Git → автоматичне оновлення у Kubernetes без ручного втручання.
