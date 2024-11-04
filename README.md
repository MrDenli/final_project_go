# Task Scheduler API

Приложение Task Scheduler API — это REST API для управления задачами с возможностью повтора. Приложение разработано на Go и использует SQLite для хранения данных.

## Структура проекта

- **main.go** — точка входа, настройка маршрутов и запуск сервера.
- **handlers.go** — обработчики HTTP-запросов, связанные с CRUD-операциями для задач.
- **db.go** — инициализация и настройка базы данных SQLite.
- **date_units.go** — функции для расчета следующих дат с учетом правил повторения.
- **web/** — директория для статических файлов веб-интерфейса (если требуется).

## Требования

- Go 1.18+
- SQLite3 (драйвер для Go)

## Установка

1. Склонируйте репозиторий:
   ```bash
   git clone https://github.com/username/task-scheduler-api.git
   cd task-scheduler-api

2. Установите зависимости:
    ```bash
    go mod tidy

## Запуск приложения

go run main.go


Сервер будет запущен по умолчанию на http://localhost:7540.

## Примеры использования

1. Получение списка задач
    ```bash
    curl -X GET http://localhost:7540/api/task

2. Добавление новой задачи
    ```bash
    curl -X POST http://localhost:7540/api/task -H "Content-Type: application/json" -d '{
        "date": "20240101",
        "title": "My Task",
        "comment": "Task description",
        "repeat": "d 7"
    }'

3. Обновление задачи
    ```bash
    curl -X PUT http://localhost:7540/api/task -H "Content-Type: application/json" -d '{
        "id": "1",
        "date": "20240101",
        "title": "Updated Task",
        "comment": "Updated description",
        "repeat": "d 1"
    }'

4. Удаление задачи
    ```bash
    curl -X DELETE "http://localhost:7540/api/task?id=1"

5. Отметка задачи выполненной
    ```bash
    curl -X POST "http://localhost:7540/api/task/done?id=1"

## Тестирование

    go test ./tests
