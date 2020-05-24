# bugtracker.getReporterProducts
Метод возвращает список продуктов пользователя

## Параметры

| Параметр    | Тип | Описание                                                                 |
|-------------|-----|--------------------------------------------------------------------------|
| reporter_id | int | ID пользователя. Необязательный                                          |
| preview     | int | Флаг. Если `1`, то в ответе будут три рандомных продукта. Необязательный |

## Пример ответа
```json
{
  "response": {
    "items": [
      {
        "id": 1,
        "title": "Product",
        "description": "Description",
        "photo": "",
        "is_available": true,
        "user_reports_count": 1,
        "reports_count": 1000,
        "wishes_reports_count": 250
      }
    ],
    "available_products_count": 75,
    "secret_products_count": 0,
    "secret_reports_count": 0,
    "uncounted_reports_count": 0,
    "unshown_reports_count": 150
  }
}
```