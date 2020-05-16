# bugtracker.getProducts
Получить продукты.

## Параметры

| Параметр | Тип    | Описание                                |
|----------|--------|-----------------------------------------|
| section  | string | Секция: `all`, `my`, `download`         |
| count    | int    | Количество продуктов. Лимит возможно 20 |
| offset   | int    | Оффсет                                  |
| platform | int    | Неизвестно. Я видел `3`                 |
| q        | string | Строка поиска                           |

## Пример ответа
```json
{
  "response": {
    "items": [
      {
        "id": 1,
        "title": "Product name",
        "description": "Description",
        "photo": "",
        "is_available": true,
        "reports_count": 1,
        "wishes_reports_count": 2
      }
    ],
    "sections": [
      {
        "id": "all"
      },
      {
        "id": "my",
        "products_count": 75
      },
      {
        "id": "download",
        "products_count": 3
      }
    ]
  }
}
```