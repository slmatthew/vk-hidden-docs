# bugtracker.editComment
Редактирование комментария.

## Параметры

| Параметры    | Тип           | Описание                             |
|--------------|---------------|--------------------------------------|
| bugreport_id | int           | ID репорта                           |
| text         | string        | Текст отредактированного комментария |
| hash         | string        | `comment.edit_hash`                  |
| comment_id   | int           | ID комментария                       |
| attachments  | array[string] | Вложения                             |

> Чтобы убрать аттачи из коммента, который был с ними, нужно не указывать attachments.

## Пример ответа
```json
{
  "response": {
    "comment": {
      "bugreport_id": 1,
      "comment_id": 2,
      "created": 1589058643,
      "text": "тест123",
      "from_id": 305360617,
      "author_name": "Матвей Вишневский",
      "author_photo": "https:\/\/sun1-94.userapi.com\/gjPybn72QpkBWzWp-JXy5AcuYutlNnr0Tuf_Ng\/45im54LHOZM.jpg?ava=1",
      "edit_hash": "",
      "remove_hash": ""
    }
  }
}
```