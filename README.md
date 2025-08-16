##
#
Відео, яке демонструє як працює додаток ArgoCD
#
[![Смотреть видео](https://andreysvirid.github.io/AsciiArtif/preview2.gif)](https://andreysvirid.github.io/AsciiArtify/demo2.mp4)

# Concept: Порівняльний аналіз інструментів для локального Kubernetes


## 1. Вступ
Стартап **AsciiArtify** планує створити сервіс для перетворення зображень у ASCII-art з використанням Machine Learning.  
Для розробки та тестування локально команда розглядає три інструменти для запуску Kubernetes:

- **minikube** — локальний кластер Kubernetes на одній машині.
- **kind** (Kubernetes IN Docker) — запуск кластерів Kubernetes у Docker.
- **k3d** — запуск кластерів Kubernetes у Docker на базі Rancher Kubernetes Engine (k3s).

---

## 2. Характеристики

| Характеристика | minikube | kind | k3d |
|----------------|----------|------|-----|
| **Підтримувані ОС** | Windows, macOS, Linux | Windows, macOS, Linux | Windows, macOS, Linux |
| **Архітектури** | x86_64, ARM | x86_64, ARM | x86_64, ARM |
| **Автоматизація (CI/CD)** | Обмежена | Добре підходить | Добре підходить |
| **Моніторинг** | Вбудований Dashboard | Потрібна інтеграція | Потрібна інтеграція |
| **Швидкість запуску** | Середня | Висока | Дуже висока |
| **Використання Docker** | Необов’язкове | Обов’язкове | Обов’язкове |
| **Альтернатива Podman** | Можлива з налаштуванням | Частково можлива | Частково можлива |
| **Масштабування** | Обмежене | Обмежене | Обмежене |

---

## 3. Переваги та недоліки

### minikube
✅ Простий старт для новачків.  
✅ Має вбудований Kubernetes Dashboard.  
⚠️ Запускається повільніше за kind/k3d.  
⚠️ Менш зручний для CI/CD.

### kind
✅ Легкий і швидкий запуск.  
✅ Ідеальний для CI/CD.  
⚠️ Немає вбудованого моніторингу — треба налаштовувати окремо.  
⚠️ Не підходить для продакшн-навантажень.

### k3d
✅ Найшвидший запуск.  
✅ Використовує полегшену версію Kubernetes — k3s.  
⚠️ Має нюанси з сумісністю деяких модулів.  
⚠️ Потребує Docker.

---

## 4. Демонстрація (рекомендований інструмент — k3d)

```bash
# Встановлення k3d
curl -s https://raw.githubusercontent.com/k3d-io/k3d/main/install.sh | bash

# Створення кластера
k3d cluster create hello-cluster

# Перевірка стану
kubectl get nodes

# Деплой Hello World
kubectl create deployment hello --image=nginxdemos/hello
kubectl expose deployment hello --type=NodePort --port=80

# Перегляд доступних сервісів
kubectl get svc hello
Відкриваємо http://<NodeIP>:<NodePort> у браузері та бачимо сторінку Hello World.

5. Висновки та рекомендації
Інструмент	Рекомендація
minikube	Для навчання та коли потрібен Dashboard без Docker.
kind	Для швидких тестів у CI/CD.
k3d	Для PoC AsciiArtify — найкраще співвідношення швидкості та зручності.

Загальна рекомендація: Для нашого PoC стартапу AsciiArtify оптимально використати k3d, оскільки він швидкий, легкий, має низькі вимоги до ресурсів і добре інтегрується з CI/CD.

6. [Переглянути відео](https://github.com/andreysvirid/AsciiArtify/blob/main/poc_video.mp4)
