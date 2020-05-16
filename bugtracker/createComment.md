# bugtracker.createComment
Отправить комментарий.

## Параметры

| Параметры    | Тип           | Описание                                       |
|--------------|---------------|------------------------------------------------|
| bugreport_id | int           | ID репорта, к которому оставляется комментарий |
| text         | string        | Текст комментария                              |
| hash         | string        | `comment_hash` из `bugtracker.getComments`     |
| attachments  | array[string] | Вложения                                       |

## Пример ответа
```json
{
  "response": {
    "comment": {
      "bugreport_id": 1,
      "comment_id": 2,
      "created": 1589058643,
      "text": "тест",
      "from_id": 305360617,
      "author_name": "Матвей Вишневский",
      "author_photo": "https:\/\/sun1-94.userapi.com\/gjPybn72QpkBWzWp-JXy5AcuYutlNnr0Tuf_Ng\/45im54LHOZM.jpg?ava=1",
      "edit_hash": "",
      "remove_hash": ""
    }
  }
}
```