# bugtracker.reproduce
Поставить отметку «Воспроизводится» или «Нравится»

## Параметры

| Параметр     | Тип    | Описание                                    |
|--------------|--------|---------------------------------------------|
| bugreport_id | int    | ID репорт                                   |
| hash         | string | `bugreport.reproduces.reproduce_hash`       |
| state        | int    | 1 - воспроизводится, 0 - не воспроизводится |

## Пример ответа
```json
{
  "response": {
    "reproduces": {
      "count": 1,
      "profiles": [
        {
          "id": 305360617,
          "first_name": "Матвей",
          "last_name": "Вишневский",
          "is_closed": false,
          "can_access_closed": true,
          "photo_50": "https:\/\/sun1-95.userapi.com\/bswxPp5CLI_p2a-rZZd1xjiudXVekZ1ak4flaQ\/tSDUGjqZaTU.jpg?ava=1",
          "photo_100": "https:\/\/sun1-18.userapi.com\/277tRs6qmz_zng9pXKUWu18p0Dd2xZfze2G4bg\/0OgGfXyvJ7A.jpg?ava=1"
        }
      ],
      "is_reproduced_by_me": true,
      "reproduce_hash": ""
    }
  }
}
```