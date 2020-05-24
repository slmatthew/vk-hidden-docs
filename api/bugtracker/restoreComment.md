# bugtracker.restoreComment
Восстановить комментарий.

## Параметры

| Параметр     | Тип    | Описание                                     |
|--------------|--------|----------------------------------------------|
| bugreport_id | int    | ID репорта                                   |
| comment_id   | int    | ID комментария                               |
| hash         | string | `restore_hash` из `bugtracker.deleteComment` |

## Пример ответа
```json
{
  "response": 1
}
```