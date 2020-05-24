# bugtracker.deleteComment
Удалить комментарий

## Параметры

| Параметры    | Тип           | Описание              |
|--------------|---------------|-----------------------|
| bugreport_id | int           | ID репорта            |
| hash         | string        | `comment.remove_hash` |
| comment_id   | int           | ID комментария        |

## Пример ответа
```json
{
  "response": {
    "restore_hash": ""
  }
}
```