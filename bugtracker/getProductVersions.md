# bugtracker.getProductVersions
Получить версии продукта.

## Параметры

| Параметр    | Тип | Описание                                        |
|-------------|-----|-------------------------------------------------|
| product_id  | int | ID продукта                                     |
| version_ids | int | ID версий                                       |
| count       | int | Количество версий                               |
| extended    | int | Флаг. Получить расширенную информацию о версиях |

## Пример ответа
extended = 0

```json
{
  "response": {
    "items": [
      {
        "id": 1,
        "product_id": 1,
        "title": "Название версии",
        "release_notes": "Описание версии",
        "date": 1589025277,
        "reports_count": 146,
        "reports_url": "/bugs?product=1&version=1&status=100&wishes=1",
        "closed_reports_count": 0,
        "closed_reports_url": "/bugs?product=1&version=1&status=5&wishes=1",
        "vulnerability_reports_count": 0
      }
    ]
  }
}
```

extended = 1

```json
{
  "response": {
    "items": [
      {
        "id": 1,
        "product_id": 1,
        "title": "Название версии",
        "release_notes": "Описание версии",
        "date": 1589025277,
        "reports_count": 146,
        "reports_url": "/bugs?product=1&version=1&status=100&wishes=1",
        "closed_reports_count": 0,
        "closed_reports_url": "/bugs?product=1&version=1&status=5&wishes=1",
        "vulnerability_reports_count": 0,
        "platform": 4,
        "download_hash": ""
      }
    ]
  }
}
```