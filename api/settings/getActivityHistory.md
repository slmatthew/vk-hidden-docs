# settings.getActivityHistory
Получить историю активности

## Параметры

| Параметр | Тип    | Описание                                                         |
|----------|--------|------------------------------------------------------------------|
| hash     | string | `history_hash` из [settings.getSecurityInfo](getSecurityInfo.md) |

## Пример ответа
```json
{
  "response": {
    "code": 241,
    "history": [
      {
        "device": "laptop",
        "platform": "Windows",
        "browser": "Браузер Firefox",
        "country": "Россия",
        "city": "Москва",
        "date": "сегодня в 23:40",
        "ip": "192.168.0.1",
        "remix_seed": "123456789",
        "photo": "https://vk.com/images/activity_history/icon_78.png"
      },
      {
        "device": "android",
        "platform": "HMD Global Nokia 5.1 Plus",
        "browser": "Приложение ВКонтакте",
        "country": "Россия",
        "city": "Москва",
        "date": "сегодня в 22:25",
        "ip": "192.168.0.1",
        "remix_seed": "12345678",
        "photo": "https://vk.com/images/activity_history/icon_78.png"
      },
      {
        "device": "unrecognized",
        "platform": "Неизвестный тип устройства",
        "browser": "Приложение slmatthew apps",
        "country": "Франция",
        "city": "",
        "date": "сегодня в 22:00",
        "ip": "192.168.0.1",
        "remix_seed": "123456789",
        "photo": "https://vk.com/images/dquestion_d.png"
      }
    ]
  }
}
```