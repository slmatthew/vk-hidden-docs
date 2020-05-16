# bugtracker.getBookmarks
Получить список отчетов в закладках

## Параметры

| Параметр | Тип | Описание           |
|----------|-----|--------------------|
| count    | int | Количество отчетов |
| offset   | int | Оффсет             |

## Пример ответа
```json
{
  "response": {
    "count": 28,
    "items": [
      {
        "id": 1,
        "title": "Название отчета",
        "owner_id": 305360617,
        "created": 1507332204,
        "updated": 1507393846,
        "status": {
          "id": 3,
          "name": "Отклонён"
        },
        "comments_count": 3,
        "product": {
          "id": 3,
          "name": "Баг-трекер"
        },
        "tags": [
          {
            "id": 8,
            "name": "Уведомления"
          }
        ],
        "reproduces": {
          "count": 0
        }
      }
    ],
    "profiles": [
      {
        "id": 305360617,
        "first_name": "Матвей",
        "last_name": "Вишневский",
        "is_closed": false,
        "can_access_closed": true
      }
    ]
  }
}
```