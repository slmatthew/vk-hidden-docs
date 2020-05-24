# bugtracker.changeBugreportStatus
Сменить статус отчёта

## Параметры

| Параметр     | Тип    | Описание                                |
|--------------|--------|-----------------------------------------|
| bugreport_id | int    | ID репорта                              |
| hash         | string | `change_status_hash` из объекта репорта |
| status       | int    | ID нового статуса отчёта                |
| comment      | string | Текст комментария                       |

## Пример ответа
```json
{
  "response": 1
}
```