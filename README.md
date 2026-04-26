Освобождаем ресурсы.

Удаляем Kustomize (dev/prod). Удаляем Helm release

![alt text](image.png)

Останавливаем tunnel

![alt text](image-1.png)

Чистим Docker
![alt text](image-2.png)
![alt text](image-3.png)

Добавляем ssh ключ
![alt text](image-4.png)

Проверяем
![alt text](image-5.png)

Создаем новый репозиторий и клонируем через ssh
![alt text](image-6.png)

![alt text](image-7.png)

Создаем приложение.

Файл приложения
![alt text](image-8.png)

Юнит-тесты
![alt text](image-9.png)

requirements.txt

![alt text](image-10.png)

Dockerfile

![alt text](image-11.png)

Сейчас тест будет падать. Сделано для демонстрации CI

Делаем тестовый pipeline

![alt text](image-12.png)

Комитим и пушим
![alt text](image-13.png)

Первый pipeline отработал правильно
![alt text](image-14.png)

Делаем боевой сценарий
```
lint → тесты → сборка → проверка
```

Нормальный CI pipeline

![alt text](image-15.png)


Pipeline упал, так как мы заранее сделали ошибку в коде
![alt text](image-16.png)

Теперь исправим ошибку и снова запушим.
![alt text](image-17.png)

Pipeline стал зеленым
![alt text](image-18.png)

Регистрируемся и создаем репозиторий в Docker
![alt text](image-19.png)

Добавляем секреты, чтобы github мог общаться с docker
![alt text](image-20.png)

Создаём release pipeline
![alt text](image-21.png)

CD публикация работает
![alt text](image-22.png)

Делаем Kubernetes-манифесты для приложения

![alt text](image-23.png)

Запускаем minikube кластер
![alt text](image-24.png)

Разворачиваем приложение в Kubernetes
![alt text](image-25.png)

Делаем minikube tunnel в отдельном терминале и проверяем
![alt text](image-26.png)

Устанавливаем ArgoCD
```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

Ждем когда все запустится
![alt text](image-27.png)

Делаем проброс
![alt text](image-28.png)

Подключаем репозиторий
![alt text](image-29.png)

Создаем приложение
![alt text](image-30.png)

Я изменил файл и запушил. CI прошли успешно
![alt text](image-31.png)

Пересоздаем контейнеры
![alt text](image-33.png)

Видим, что вторая версия работает
![alt text](image-34.png)

Argo полностью управляет приложением
![alt text](image-35.png)