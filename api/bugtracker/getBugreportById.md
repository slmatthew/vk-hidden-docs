# bugtracker.getBugreportById
Получить репорт по его ID.

## Параметры

| Параметр     | Тип    | Описание                        |
|--------------|--------|---------------------------------|
| bugreport_id | int    | ID репорта                      |
| fields       | string | https://vk.com/dev/objects/user |

## Пример ответа
```json
{
  "response": {
    "bugreport": {
      "id": 1,
      "title": "Тест",
      "owner_id": 305360617,
      "created": 1565715875,
      "updated": 1571575826,
      "status": {
        "id": 2,
        "name": "Исправлен"
      },
      "description": "Шаги воспроизведения",
      "state_actual": "Фактический результат",
      "state_supposed": "Ожидаемый результат",
      "attachments": [
        {
          "type": "photo",
          "photo": {}
        }
      ],
      "comments_count": 3,
      "unsubscribe_hash": "",
      "is_subscribed": true,
      "bookmark_hash": "",
      "issue_type": {
        "id": 6,
        "name": "Косметическое несоответствие"
      },
      "severity": {
        "id": 1,
        "name": "Низкий"
      },
      "is_severity_by_moderator": true,
      "product": {
        "id": 1,
        "name": "Product name"
      },
      "product_version": {
        "id": 186,
        "name": "Version name"
      },
      "product_actual_version": {
        "id": 186,
        "name": "Version name"
      },
      "platforms": [
        {
          "id": 1,
          "name": "Windows"
        }
      ],
      "platforms_versions": [],
      "tags": [
        {
          "id": 85,
          "name": "Комментарии"
        },
        {
          "id": 181,
          "name": "Статьи"
        }
      ],
      "user_devices": [
        {
          "id": 1,
          "status": 0,
          "title": "Device",
          "platform": {
            "id": 1,
            "name": "Windows"
          },
          "model": "Model",
          "user_device_id": 483300000
        }
      ],
      "reproduces": {
        "count": 1,
        "profiles": [
          {
            "id": 408091805,
            "first_name": "Глеб",
            "last_name": "Фараонов",
            "is_closed": false,
            "can_access_closed": true,
            "photo_50": "https://sun9-38.userapi.com/c858020/v858020062/5c30f/o4_KIcKAs-8.jpg?ava=1",
            "photo_100": "https://sun9-55.userapi.com/c858020/v858020062/5c30e/ACB9ios-7UY.jpg?ava=1"
          }
        ]
      }
    },
    "profiles": [
      {
        "id": 305360617,
        "first_name": "Матвей",
        "last_name": "Вишневский",
        "is_closed": false,
        "can_access_closed": true
      }
    ]
  }
}
```