# REST API — Lab 2

Base URL: `http://localhost:1880`

## GET /api/text

Возвращает простой текст.

**Запрос:** `curl http://localhost:1880/api/text`

**Ответ 200:**
```
Дарова! Это /api/text
```

## GET /api/info

Возвращает JSON с информацией.

**Запрос:** `curl http://localhost:1880/api/info`

**Ответ 200:**
```json
{
    "author": "safonchik",
    "lab": "lab2",
    "time": "2026-10-09T12:34:56.789Z"
}
```

## GET /api/items/:category

Возвращает список элементов указанной категории.

**Path-параметр:**
- `category` — `books` | `movies` | `games`

**Query-параметр:**
- `limit` — число элементов (по умолчанию 10)

**Успешный запрос:**
```
curl http://localhost:1880/api/items/books
```

**Ответ 200:**
```json
{
    "category": "books",
    "count": 10,
    "items": [
        { "id": 1, "name": "books-1", "author": "safonchik" },
        { "id": 2, "name": "books-2", "author": "safonchik" }
    ]
}
```

**Ошибка 404 — категория не найдена:**
```
curl -i http://localhost:1880/api/items/unknown
```

**Ответ:**
```
HTTP/1.1 404 Not Found
Content-Type: application/json; charset=utf-8
```
```json
{
    "error": "Not Found",
    "message": "Категория 'unknown' не существует",
    "allowed": ["books", "movies", "games"]
}
```
