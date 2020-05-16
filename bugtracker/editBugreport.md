# bugtracker.editBugreport
Отредактировать репорт или создать новый.

## Параметр

| Параметр     | Тип | Описание                                                              |
|--------------|-----|-----------------------------------------------------------------------|
| bugreport_id | int | ID репорта. Если не передать этот параметр, будет создан новый репорт |

## Пример ответа
```json
{
  "response": {
    "bugreport": {
      "id": 0,
      "title": "",
      "description": "",
      "state_actual": "",
      "state_supposed": "",
      "product_id": 1,
      "confidential": false,
      "severity": 2,
      "issue_type": 0,
      "attachments": [],
      "tags": [],
      "user_devices": [
        483360000
      ],
      "platforms": [
        1,
        4
      ],
      "platforms_versions": [
        10012
      ]
    },
    "products": [
      {
        "id": 22,
        "name": "VK API",
        "version": "5.103",
        "tags": [
          {
            "id": 119,
            "name": "Account (работа с аккаунтом)"
          },
          {
            "id": 120,
            "name": "Ads (реклама)"
          },
          {
            "id": 121,
            "name": "Apps (приложения)"
          },
          {
            "id": 122,
            "name": "Board (обсуждения)"
          },
          {
            "id": 170,
            "name": "Callback API"
          },
          {
            "id": 123,
            "name": "Database (учебные заведения)"
          },
          {
            "id": 124,
            "name": "Docs (документы)"
          },
          {
            "id": 171,
            "name": "Execute  (Универсальный метод)"
          },
          {
            "id": 125,
            "name": "Fave (закладки)"
          },
          {
            "id": 126,
            "name": "Friends (друзья)"
          },
          {
            "id": 127,
            "name": "Gifts (подарки)"
          },
          {
            "id": 128,
            "name": "Groups (сообщества)"
          },
          {
            "id": 129,
            "name": "Leads (рекламные акции)"
          },
          {
            "id": 130,
            "name": "Likes (лайки)"
          },
          {
            "id": 131,
            "name": "Market (товары)"
          },
          {
            "id": 132,
            "name": "Messages (сообщения)"
          },
          {
            "id": 133,
            "name": "Newsfeed (новостная лента)"
          },
          {
            "id": 134,
            "name": "Notes (заметки)"
          },
          {
            "id": 135,
            "name": "Notifications (оповещения)"
          },
          {
            "id": 149,
            "name": "Orders (заказы в платежном API)"
          },
          {
            "id": 136,
            "name": "Pages (wiki-страницы)"
          },
          {
            "id": 137,
            "name": "Photos (фотографии)"
          },
          {
            "id": 138,
            "name": "Places (места)"
          },
          {
            "id": 139,
            "name": "Polls (опросы)"
          },
          {
            "id": 140,
            "name": "Search (поиск)"
          },
          {
            "id": 141,
            "name": "Secure (серверные методы приложения)"
          },
          {
            "id": 142,
            "name": "Stats (статистика)"
          },
          {
            "id": 143,
            "name": "Status (работа со статусом)"
          },
          {
            "id": 308,
            "name": "Stories (истории)"
          },
          {
            "id": 148,
            "name": "Streaming (Streaming API)"
          },
          {
            "id": 145,
            "name": "Users (данные пользователя)"
          },
          {
            "id": 146,
            "name": "Utils (служебные методы)"
          },
          {
            "id": 147,
            "name": "Video (видео)"
          },
          {
            "id": 150,
            "name": "Wall (стена)"
          },
          {
            "id": 151,
            "name": "Widgets (виджеты на внешних сайтах)"
          },
          {
            "id": 152,
            "name": "oAuth (авторизация через API)"
          },
          {
            "id": 356,
            "name": "Документация"
          },
          {
            "id": 233,
            "name": "Сервисы"
          }
        ],
        "platforms": [
          {
            "id": 1,
            "name": "Windows"
          },
          {
            "id": 2,
            "name": "MacOS"
          },
          {
            "id": 3,
            "name": "iOS"
          },
          {
            "id": 4,
            "name": "Android"
          },
          {
            "id": 5,
            "name": "Linux"
          }
        ],
        "platforms_versions": [
          {
            "id": 1,
            "name": "iOS 8"
          },
          {
            "id": 2,
            "name": "iOS 9"
          },
          {
            "id": 3,
            "name": "iOS 10"
          },
          {
            "id": 4,
            "name": "iOS 11"
          },
          {
            "id": 5,
            "name": "iOS 12"
          },
          {
            "id": 6,
            "name": "iOS 13"
          },
          {
            "id": 10001,
            "name": "4.1 Jelly Bean"
          },
          {
            "id": 10002,
            "name": "4.2 Jelly Bean"
          },
          {
            "id": 10003,
            "name": "4.3 Jelly Bean"
          },
          {
            "id": 10004,
            "name": "4.4 KitKat"
          },
          {
            "id": 10005,
            "name": "5.0 Lollipop"
          },
          {
            "id": 10006,
            "name": "5.1 Lollipop"
          },
          {
            "id": 10007,
            "name": "6.0 Marshmallow"
          },
          {
            "id": 10008,
            "name": "7.0 Nougat"
          },
          {
            "id": 10009,
            "name": "7.1 Nougat"
          },
          {
            "id": 10010,
            "name": "8.0 Oreo"
          },
          {
            "id": 10011,
            "name": "8.1 Oreo"
          },
          {
            "id": 10012,
            "name": "9.0 P"
          },
          {
            "id": 10013,
            "name": "10.0 Q"
          }
        ]
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
      },
      {
        "id": 2,
        "status": 0,
        "title": "Device",
        "platform": {
          "id": 4,
          "name": "Android"
        },
        "model": "Model",
        "platform_version": {
          "id": 10012,
          "name": "9.0 P"
        },
        "user_device_id": 483300000
      }
    ],
    "severities": [
      {
        "id": 1,
        "name": "Низкий"
      },
      {
        "id": 2,
        "name": "Средний"
      },
      {
        "id": 3,
        "name": "Высокий"
      },
      {
        "id": 4,
        "name": "Критический"
      },
      {
        "id": 5,
        "name": "Уязвимость"
      }
    ],
    "issue_types": [
      {
        "id": 1,
        "name": "Падение приложения",
        "description": "Падения приложения, блокирующие его дальнейшую работу или тестирование "
      },
      {
        "id": 2,
        "name": "Зависание приложения",
        "description": "Зависания приложения, блокирующие его дальнейшую работу или тестирование "
      },
      {
        "id": 3,
        "name": "Неработающая функциональность",
        "description": "Неработающая или неверно работающая функциональность. Например, не отправить сообщение, не удалить фотографию. "
      },
      {
        "id": 4,
        "name": "Потеря данных",
        "description": "Потеряны или испорчены все (часть) данных пользователя "
      },
      {
        "id": 5,
        "name": "Производительность",
        "description": "Время отклика на действия пользователя "
      },
      {
        "id": 6,
        "name": "Косметическое несоответствие",
        "description": "Проблемы с отображением элементов и данных на экране "
      },
      {
        "id": 7,
        "name": "Ошибка в тексте",
        "description": "Грамматические, орфографические, синтаксические ошибки, проблемы локализации. "
      },
      {
        "id": 8,
        "name": "Пожелание",
        "description": "Изменения, которые, по Вашему мнению, стоит внести, чтобы улучшить пользовательский опыт "
      }
    ],
    "platforms": [
      {
        "id": 1,
        "name": "Windows",
        "versions": []
      },
      {
        "id": 2,
        "name": "MacOS",
        "versions": []
      },
      {
        "id": 3,
        "name": "iOS",
        "versions": [
          {
            "id": 6,
            "name": "iOS 13"
          },
          {
            "id": 5,
            "name": "iOS 12"
          },
          {
            "id": 4,
            "name": "iOS 11"
          },
          {
            "id": 3,
            "name": "iOS 10"
          },
          {
            "id": 2,
            "name": "iOS 9"
          },
          {
            "id": 1,
            "name": "iOS 8"
          }
        ]
      },
      {
        "id": 4,
        "name": "Android",
        "versions": [
          {
            "id": 10013,
            "name": "10.0 Q"
          },
          {
            "id": 10012,
            "name": "9.0 P"
          },
          {
            "id": 10011,
            "name": "8.1 Oreo"
          },
          {
            "id": 10010,
            "name": "8.0 Oreo"
          },
          {
            "id": 10009,
            "name": "7.1 Nougat"
          },
          {
            "id": 10008,
            "name": "7.0 Nougat"
          },
          {
            "id": 10007,
            "name": "6.0 Marshmallow"
          },
          {
            "id": 10006,
            "name": "5.1 Lollipop"
          },
          {
            "id": 10005,
            "name": "5.0 Lollipop"
          },
          {
            "id": 10004,
            "name": "4.4 KitKat"
          },
          {
            "id": 10003,
            "name": "4.3 Jelly Bean"
          },
          {
            "id": 10002,
            "name": "4.2 Jelly Bean"
          },
          {
            "id": 10001,
            "name": "4.1 Jelly Bean"
          }
        ]
      },
      {
        "id": 5,
        "name": "Linux",
        "versions": []
      }
    ],
    "hash": ""
  }
}
```