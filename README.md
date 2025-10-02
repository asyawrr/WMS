# API Tests with Newman

Этот проект содержит автоматические тесты Postman, которые выполняются с помощью [Newman](https://github.com/postmanlabs/newman) и GitHub Actions.  
Результаты прогонов тестов публикуются как HTML-отчёты через **GitHub Pages**.

## 🚀 Функционал
- Хранение Postman коллекций и окружений в репозитории.
- Автоматический запуск тестов:
  - по расписанию (ежедневно в 03:00 UTC);
  - при push в ветку `main`;
  - вручную через кнопку `Run workflow`.
- Генерация отчётов (`htmlextra`).
- Автоматическая публикация отчётов на GitHub Pages.

## 📂 Структура проекта
```
collections/                # Postman коллекции
Collection.postman_collection.json
environment/                # Окружения Postman
dev-env.json
reports/                    # Папка для HTML отчётов (автоматически создаётся в CI)
.github/workflows/ci.yml    # Workflow для GitHub Actions
```

## ▶️ Локальный запуск
1. Установи [Node.js 18+](https://nodejs.org/).
2. Установи Newman и репортёр:
   ```bash
   npm install -g newman newman-reporter-htmlextra
3. Запустить коллекцию

```
newman run collections/Collection.postman_collection.json \
  -e environment/dev-env.json \
  -r cli,htmlextra \
  --reporter-htmlextra-export reports/report.html
```

## ⚙️ CI/CD

Файл `.github/workflows/ci.yml` запускает тесты в GitHub Actions.
После прогона отчёт сохраняется в артефакты и публикуется в GitHub Pages.

## 🌐 Отчёты

После успешного деплоя отчёт доступен по адресу: `https://asyawrr.github.io/WMS/`
