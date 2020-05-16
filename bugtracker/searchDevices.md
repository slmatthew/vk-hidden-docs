# bugtracker.searchDevices
Поиск девайса

## Параметры

| Параметр | Тип    | Описание      |
|----------|--------|---------------|
| q        | string | Строка поиска |

## Пример ответа
```json
{
  "response": {
    "items": [
      {
        "id": 17423,
        "status": 0,
        "title": "Apple Macbook Air 13 inch",
        "platform": {
          "id": 2,
          "name": "MacOS"
        },
        "model": "Macbook Air 13 inch 2013",
        "add_hash": ""
      }
    ],
    "save_device_hash": ""
  }
}
```