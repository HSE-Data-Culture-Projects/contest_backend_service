# Yandex Contest API Handler

Микросервис-прослойка для взаимодействия с API Яндекс.Контеста: получение задач и их описаний, списка компиляторов, отправка решений и получение отчёта о проверке.

## Основные возможности

* **Получение задач**: `GET /api/contests/:contestId/problems`
* **Получение условия задачи**: `GET /api/contests/:contestId/problems/:problemId/statement`
* **Список компиляторов**: `GET /api/compilers`
* **Отправка решения**: `POST /api/contests/:contestId/submissions`

  * Код можно передать полем `code` и `extension` или загрузить файл через multipart/form-data
  * Сервис ожидает завершения проверки и возвращает полный отчёт
* **Получение полного отчёта посылки**: `GET /api/contests/:contestId/submissions/:submissionId/full`
* Логирование всех операций через **Winston**

## Требования

* Node.js v16+
* npm v6+

## Установка и запуск

1. Клонировать репозиторий:

   ```bash
   git clone <repo_url>
   cd yandex-contest-api
   ```
2. Установить зависимости:

   ```bash
   npm install
   ```
3. Создать файл `.env` в корне проекта и задать токен:

   ```env
   TOKEN=ВашOAuthтокенЯндексКонтеста
   ```
4. Запустить сервис:

   ```bash
   npm start
   ```

Сервис будет слушать порт **3000**.

## Конфигурация через Docker

* В проекте есть `Dockerfile` и `docker-compose.yml`.
* Для запуска в контейнере:

  ```bash
  docker-compose up --build
  ```

По умолчанию сервис будет доступен на `http://localhost:3002`.

## Структура проекта

```
├── src/
│   ├── server.js         # Точка входа (Express)
│   ├── routes.js         # Определение маршрутов
│   ├── controllers.js    # Логика работы с API Яндекс.Контеста
│   ├── logger.js         # Настройка Winston
│   └── config.js         # Чтение переменных окружения
├── Dockerfile
├── docker-compose.yml
├── package.json
└── .env.example
```

## Лицензия

Проект распространяется под лицензией **ISC**.
