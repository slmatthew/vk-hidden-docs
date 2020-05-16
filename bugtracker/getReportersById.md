# bugtracker.getReportersById
Получить карточки тестировщиков.

## Параметры

| Параметр     | Тип    | Значение                                                            |
|--------------|--------|---------------------------------------------------------------------|
| reporter_ids | string | Числовые ID пользователей через запятую. Максимум 100 пользователей |
| fields       | string | https://vk.com/dev/objects/user                                     |
| extended     | int    | Флаг. Если `1`, то будет возвращена сетка активности                |

## Пример ответа
```json
{
  "response": {
    "items": [
      {
        "id": 1,
        "status_text": "Не участвует в программе VK Testers",
        "reports_count": 0,
        "top_position": 0
      },
      {
        "id": 305360617,
        "status_text": "#129 в общем рейтинге, 168 отчётов",
        "reports_count": 168,
        "top_position": 129
      }
    ],
    "profiles": [
      {
        "id": 1,
        "first_name": "Павел",
        "last_name": "Дуров",
        "is_closed": false,
        "can_access_closed": true
      },
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