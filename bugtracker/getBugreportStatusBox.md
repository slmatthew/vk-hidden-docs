# bugtracker.getBugreportStatusBox
Получить данные для блока, через который нужно менять статус отчёта.

## Параметры

| Параметры    | Тип    | Описание                                |
|--------------|--------|-----------------------------------------|
| bugreport_id | int    | ID репорта                              |
| hash         | string | `change_status_hash` из объекта репорта |

## Пример ответа
```json
{
  "response": {
    "current_status": 5,
    "suggested_status": 5,
    "statuses": [
      {
        "id": 5,
        "name": "Закрыт"
      },
      {
        "id": 7,
        "name": "Переоткрыт"
      }
    ],
    "status_comment_required": [
      7
    ]
  }
}
```