# bugtracker.getComments
Получить комментарии к репорту.

## Параметры

| Параметр     | Тип | Описание                              |
|--------------|-----|---------------------------------------|
| bugreport_id | int | ID репорта                            |
| count        | int | Количество комментариев. Максимум 100 |

## Пример ответа
```json
{
  "response": {
    "count": 3,
    "items": [
      {
        "bugreport_id": 1,
        "comment_id": 1,
        "created": 1565802934,
        "text": "",
        "meta_text": "Новый статус отчёта – <b>В работе</b>\nПриоритет отчёта – <b>Низкий</b>",
        "author_name": "Модератор  #100",
        "author_photo": "https://vk.com/images/support15_specagent.png"
      },
      {
        "bugreport_id": 1,
        "comment_id": 2,
        "created": 1567123404,
        "text": "актуально",
        "from_id": 520163559,
        "author_name": "Еремей Иванов",
        "author_photo": "https://sun1-97.userapi.com/c854424/v854424047/2161a4/-ptEqZuMMCg.jpg?ava=1"
      },
      {
        "bugreport_id": 1,
        "comment_id": 3,
        "created": 1571575827,
        "text": "",
        "meta_text": "Новый статус отчёта – <b>Исправлен</b>",
        "author_name": "Модератор  #100",
        "author_photo": "https://vk.com/images/support15_specagent.png"
      }
    ],
    "comment_hash": ""
  }
}
```