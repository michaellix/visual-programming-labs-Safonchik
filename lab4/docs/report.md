# Лабораторная работа №4. n8n


## 1. Краткое описание выполненного
В ходе лабораторной работы на базовом уровне я освоил платформу автоматизации n8n. 
- n8n развернут локально через Docker с использованием двух volume для сохранения данных и файлов.
- Освоены базовые и продвинутые ноды: Manual Trigger, Set (Edit Fields), Code, IF, HTTP Request, Schedule Trigger, NoOp, Redis.
- Настроено подключение к Redis (через Docker) и реализованы workflow для создания/чтения и удаления/проверки ключей.
- Выполнена ачивка.

## 2. Использованные AI-промпты
1. *«Как запустить n8n в Docker на macOS, чтобы сохранялись данные, но не было ошибок доступа к папкам (permission denied)?»*
2. *«В новой версии n8n нет операции Exists для Redis. Как проверить, что ключ удален?»*

## 3. Освоенные ноды
- **Manual Trigger**: ручной запуск.
- **Set (Edit Fields)**: создание и изменение полей (payload, topic, timestamp).
- **Code (JavaScript)**: написание скриптов (let/const, if/else, циклы, объекты).
- **IF**: ветвление потоков по условию (проверка строки на вхождение).
- **HTTP Request**: GET-запросы к публичному API.
- **Schedule Trigger**: запуск по расписанию.
- **Redis**: операции Set, Get, Delete.
- **NoOp**: пустая операция для завершения ветки.
- **Webhook + Write Binary File**: для реализации REST API (ачивка).

## 4. Скриншоты workflow

*   **Запуск в Docker:** ![docker-run](screenshots/docker-run.png)
*   **Flow 01 (Manual-Set-Code):** ![flow-01](screenshots/flow-01-manual-set.png), Результат: ![flow-01-out](screenshots/flow-01-manual-set-output.png)
*   **Flow 02 (Code):** ![flow-02](screenshots/flow-02-code.png), Результат: ![flow-02-out](screenshots/flow-02-code-output.png)
*   **Flow 03 (IF):** ![flow-03](screenshots/flow-03-if.png), Результат: ![flow-03-out](screenshots/flow-03-if-output.png)
*   **Flow 04 (Set):** ![flow-04](screenshots/flow-04-set.png), Результат: ![flow-04-out](screenshots/flow-04-set-output.png)
*   **Flow 05 (HTTP):** ![flow-05](screenshots/flow-05-http.png), Результат: ![flow-05-out](screenshots/flow-05-http-output.png)
*   **Flow 06 (Schedule):** ![flow-06](screenshots/flow-06-schedule.png), Результат: ![flow-06-out](screenshots/flow-06-schedule-output.png)
*   **Flow 09 (Redis Set/Get):** ![flow-09](screenshots/flow-09-redis.png), Результат: ![flow-09-out](screenshots/flow-09-redis-output.png)
*   **Flow 10 (Redis Delete/Get):** ![flow-10](screenshots/flow-10-redis.png), Результат: ![flow-10-out](screenshots/flow-10-redis-output.png)

## 5. Выполнение ачивки 5.3: REST API для заметок на .json-файле

**Что сделано:** 
Реализован REST API, который принимает POST-запросы с текстом заметки и сохраняет их в формате JSON. Для хранения используется .json-файл внутри Docker-контейнера n8n.

**Архитектура Workflow:**
1. Webhook (POST /notes) - принимает входящий JSON-запрос с текстом заметки.
2. Code (JavaScript) — извлекает текст из тела запроса, формирует объект с уникальным ID и датой, и преобразует его в бинарный формат (Base64), чтобы узел файловой системы мог его сохранить.
3. Read/Write Files from Disk — записывает полученные данные в файл по пути /data/notes.json.
4. Respond to Webhook — возвращает клиенту успешный JSON-ответ: {"status": "success", "message": "Note saved successfully"}.

**Как проверял:**
1. Workflow был запущен в тестовом режиме (Execute workflow).
2. Через терминал macOS был отправлен POST-запрос с помощью утилиты curl:
   curl -X POST http://localhost:5678/webhook-test/notes \
     -H "Content-Type: application/json" \
     -d '{"note": "Моя первая заметка Safonchik через API!"}'
3. API успешно вернул статус success.
4. Так как Docker на macOS иногда ограничивает прямую запись в проброшенные папки хост-системы, для получения файла на локальном компьютере использовалась команда копирования из контейнера:
   docker cp n8n-lab4:/data/notes.json ./lab4/docker-files/notes.json
5. Файл notes.json был успешно скопирован в папку проекта на Mac, его содержимое проверено через cat.

**Скриншоты:**
* Схема Workflow: ![Схема](screenshots/11-achievement-api-scheme.png)
* Успешный ответ API в терминале и содержимое файла notes.json: ![Curl](screenshots/11-achievement-api-curl.png)


## 5. Выводы
В ходе работы я научился разворачивать n8n в изолированной среде Docker.  n8n позволяет быстро создавать интеграции: от простых скриптов на JS до взаимодействия с базами данных (Redis) и внешними API. Также я разобрался, как работают триггеры (ручные и по расписанию) и как передаются данные между узлами (в формате JSON). 
