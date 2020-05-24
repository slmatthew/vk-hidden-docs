# bugtracker.getReportersTop
Получить топ участников

## Параметры

| Параметр | Тип    | Описание                             |
|----------|--------|--------------------------------------|
| count    | int    | Количество участников. Минимум 10    |
| fields   | string | https://vk.com/dev/objects/user      |
| sort     | string | Тип сортировки: `rate` или `reports` |
| q        | string | Строка поиска                        |

## Пример ответа
```json
{
  "response": {
    "items": [
      {
        "id": 1,
        "rating": 29000,
        "reports_count": 4000
      }
    ],
    "profiles": [
      {
        "id": 1,
        "first_name": "Имя",
        "last_name": "Фамилия",
        "is_closed": false,
        "can_access_closed": true
      }
    ]
  }
}
```