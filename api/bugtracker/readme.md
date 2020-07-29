# bugtracker

Методы для работы с баг-трекером

## Доступ

Для доступа к этим методам нужен токен от приложения `Мобильный баг-трекер` с ID `6831669`.

Чтобы получить токен, нужно перейти по
[этой](https://oauth.vk.com/authorize?client_id=6831669&redirect_uri=https://oauth.vk.com/blank.html&display=page&response_type=token)
ссылке и после редиректа скопировать токен из ссылки.



## Типы данных

### VKSimpleItem

[bugtracker.editBugreport](#bugtrackereditbugreport): поле `description` есть у объекта типа проблемы (`issue_type`),
а `versions` — у объекта платформы (`platform`).

```ts
interface VKSimpleItem {
  id: number
  name: string
  description?: string
  versions?: VKSimpleItem[]
}
```

### VKDevice

```ts
interface VKDevice {
  id: number
  status: number
  title: string
  platform: VKSimpleItem
  model: string
  platform_version: VKSimpleItem
  user_device_id: number
  edit_hash?: string
  remove_hash?: string
}
```

### VKComment

Если не указан `from_id`, то комментарий оставлен модератором.
В `meta_text` может быть информация об измененном статусе отчета или о его новом приоритете.

```ts
interface VKComment {
  bugreport_id: number
  comment_id: number
  created: number
  text: string
  from_id?: number
  meta_text?: string
  author_name: string
  author_photo: string
  edit_hash?: string
  remove_hash?: string
}
```

### VKBugreport

```ts
interface VKBugreport {
  id: number
  title: string
  owner_id: number
  created: number
  updated: number
  status?: VKSimpleItem
  description?: string
  state_actual?: string
  state_supposed?: string
  attachments?: VKAttachment[]
  comments_count: number
  unsubscribe_hash?: string
  is_subscribed?: boolean
  bookmark_hash?: string
  issue_type?: VKSimpleItem
  severity?: VKSimpleItem
  is_severity_by_moderator?: boolean
  product: VKSimpleItem
  product_version?: VKSimpleItem
  product_actual_version?: VKSimpleItem
  platforms?: VKSimpleItem[]
  platforms_versions?: VKSimpleItem[]
  tags: VKSimpleItem[]
  user_devices?: VKDevice[]
  reproduces: {
    count: number
    profiles?: VKUser[]
  }
}
```

### VKProduct

```ts
interface VKProduct {
  id: number
  name: string
  version: string
  tags: VKSimpleItem[]
  platforms: VKSimpleItem[]
  platforms_versions: VKSimpleItem[]
}
```



## Список методов

* [bugtracker.addUserDevice](#bugtrackeradduserdevice)
* [bugtracker.bookmark](#bugtrackerbookmark)
* [bugtracker.changeBugreportStatus](#bugtrackerchangebugreportstatus)
* [bugtracker.createComment](#bugtrackercreatecomment)
* [bugtracker.deleteComment](#bugtrackerdeletecomment)
* [bugtracker.deleteUserDevice](#bugtrackerdeleteuserdevice)
* [bugtracker.editBugreport](#bugtrackereditbugreport)
* [bugtracker.editComment](#bugtrackereditcomment)
* [bugtracker.getBookmarks](#bugtrackergetbookmarks)
* [bugtracker.getBugreportById](#bugtrackergetbugreportbyid)
* [bugtracker.getBugreportSectionList](#bugtrackergetbugreportsectionlist)
* [bugtracker.getBugreportStatusBox](#bugtrackergetbugreportstatusbox)
* [bugtracker.getComments](#bugtrackergetcomments)
* [bugtracker.getDownloadVersionUrl](#bugtrackergetdownloadversionurl)
* [bugtracker.getEditDeviceFormData](#bugtrackergeteditdeviceformdata)
* [bugtracker.getInfo](#bugtrackergetinfo)
* [bugtracker.getProductBranches](#bugtrackergetproductbranches)
* [bugtracker.getProductVersions](#bugtrackergetproductversions)
* [bugtracker.getProducts](#bugtrackergetproducts)
* [bugtracker.getProductsById](#bugtrackergetproductsbyid)
* [bugtracker.getReporterProducts](#bugtrackergetreporterproducts)
* [bugtracker.getReportersById](#bugtrackergetreportersbyid)
* [bugtracker.getReportersTop](#bugtrackergetreporterstop)
* [bugtracker.getSearchParameters](#bugtrackergetsearchparameters)
* [bugtracker.getSettings](#bugtrackergetsettings)
* [bugtracker.joinProduct](#bugtrackerjoinproduct)
* [bugtracker.leaveProduct](#bugtrackerleaveproduct)
* [bugtracker.removeBugreport](#bugtrackerremovebugreport)
* [bugtracker.reproduce](#bugtrackerreproduce)
* [bugtracker.restoreComment](#bugtrackerrestorecomment)
* [bugtracker.saveBugreport](#bugtrackersavebugreport)
* [bugtracker.saveDevice](#bugtrackersavedevice)
* [bugtracker.saveUserDevice](#bugtrackersaveuserdevice)
* [bugtracker.searchBugreports](#bugtrackersearchbugreports)
* [bugtracker.searchDevices](#bugtrackersearchdevices) — Поиск устройств или получение популярных устройств
* [bugtracker.setProductVersionNotify](#bugtrackersetproductversionnotify)
* [bugtracker.updateBugreportVersion](#bugtrackerupdatebugreportversion)



## bugtracker.addUserDevice

Добавить устройства

### Параметры

| Параметр  | Тип    | Описание      |
|-----------|--------|---------------|
| device_id | int    | ID устройства |
| hash      | string | `add_hash`    |

### Тип возвращаемого значения

```ts
interface BugtrackerAddUserDevice {
  can_add_device: boolean
  device: VKDevice
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "can_add_device": true,
    "device": {
      "id": 1,
      "status": 0,
      "title": "Device",
      "platform": {
        "id": 4,
        "name": "Android"
      },
      "model": "Model",
      "platform_version": {
        "id": 10007,
        "name": "6.0 Marshmallow"
      },
      "user_device_id": 483300000,
      "edit_hash": "",
      "remove_hash": ""
    }
  }
  ```
</details>



## bugtracker.bookmark

Добавить отчёт в закладки или удалить его оттуда.

### Параметры

| Параметр     | Тип    | Описание                           |
|--------------|--------|------------------------------------|
| bugreport_id | int    | ID репорта                         |
| hash         | string | `bookmark_hash` из объекта репорта |

### Тип возвращаемого значения

```ts
interface BugtrackerBookmark {
  is_bookmarked: boolean
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  { "is_bookmarked": true }
  ```
</details>



## bugtracker.changeBugreportStatus

Сменить статус отчёта

### Параметры

| Параметр     | Тип    | Описание                                |
|--------------|--------|-----------------------------------------|
| bugreport_id | int    | ID репорта                              |
| hash         | string | `change_status_hash` из объекта репорта |
| status       | int    | ID нового статуса отчёта                |
| comment      | string | Текст комментария                       |

### Тип возвращаемого значения

```ts
type BugtrackerChangeBugreportStatus = 1;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  1
  ```
</details>



## bugtracker.createComment

Отправить комментарий.

### Параметры

| Параметры    | Тип           | Описание                                       |
|--------------|---------------|------------------------------------------------|
| bugreport_id | int           | ID репорта, к которому оставляется комментарий |
| text         | string        | Текст комментария                              |
| hash         | string        | `comment_hash` из `bugtracker.getComments`     |
| attachments  | array[string] | Вложения                                       |

### Тип возвращаемого значения

```ts
interface BugtrackerCreateComment {
  comment: VKComment
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
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
  ```
</details>



## bugtracker.deleteComment

Удалить комментарий

### Параметры

| Параметры    | Тип           | Описание              |
|--------------|---------------|-----------------------|
| bugreport_id | int           | ID репорта            |
| hash         | string        | `comment.remove_hash` |
| comment_id   | int           | ID комментария        |

### Тип возвращаемого значения

```ts
interface BugtrackerDeleteComment {
  restore_hash: string
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "restore_hash": ""
  }
  ```
</details>



## bugtracker.deleteUserDevice

Удалить устройство

### Параметры

| Параметр       | Тип    | Описание      |
|----------------|--------|---------------|
| user_device_id | int    | ID устройства |
| hash           | string | `remove_hash` |

### Тип возвращаемого значения

```ts
interface BugtrackerDeleteUserDevice {
  can_add_device: boolean
  platform_ids: number[]
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "can_add_device": true,
    "platform_ids": [ 1 ]
  }
  ```
</details>



## bugtracker.editBugreport

Отредактировать репорт или создать новый.

### Параметр

| Параметр     | Тип | Описание                                                              |
|--------------|-----|-----------------------------------------------------------------------|
| bugreport_id | int | ID репорта. Если не передать этот параметр, будет создан новый репорт |

### Тип возвращаемого значения

```ts
interface BugtrackerEditBugreport {
  bugreport: {
    id: number
    title: string
    description: string
    state_actual: string
    state_supposed: string
    product_id: number
    confidential: boolean
    severity: number
    issue_type: number
    attachments: VKAttachment[]
    tags: number[]
    user_devices: number[]
    platforms: number[]
    platforms_versions: number[]
  }
  products: VKProduct[]
  user_devices: VKDevice[]
  severities: VKSimpleItem[]
  issue_types: VKSimpleItem[]
  platforms: VKSimpleItem[]
  hash: string
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
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
  ```
</details>



## bugtracker.editComment

Редактирование комментария.

### Параметры

| Параметры    | Тип           | Описание                             |
|--------------|---------------|--------------------------------------|
| bugreport_id | int           | ID репорта                           |
| text         | string        | Текст отредактированного комментария |
| hash         | string        | `comment.edit_hash`                  |
| comment_id   | int           | ID комментария                       |
| attachments  | array[string] | Вложения                             |

> Чтобы убрать аттачи из коммента, который был с ними, нужно не указывать attachments.

### Тип возвращаемого значения

```ts

```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
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
  ```
</details>



## bugtracker.getBookmarks

Получить список отчетов в закладках

### Параметры

| Параметр | Тип | Описание           |
|----------|-----|--------------------|
| count    | int | Количество отчетов |
| offset   | int | Оффсет             |

### Тип возвращаемого значения

```ts

```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "count": 28,
    "items": [
      {
        "id": 1,
        "title": "Название отчета",
        "owner_id": 305360617,
        "created": 1507332204,
        "updated": 1507393846,
        "status": {
          "id": 3,
          "name": "Отклонён"
        },
        "comments_count": 3,
        "product": {
          "id": 3,
          "name": "Баг-трекер"
        },
        "tags": [
          {
            "id": 8,
            "name": "Уведомления"
          }
        ],
        "reproduces": {
          "count": 0
        }
      }
    ],
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
  ```
</details>



## bugtracker.getBugreportById

Получить репорт по его ID.

### Параметры

| Параметр     | Тип    | Описание                        |
|--------------|--------|---------------------------------|
| bugreport_id | int    | ID репорта                      |
| fields       | string | https://vk.com/dev/objects/user |

### Тип возвращаемого значения

```ts

```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
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
  ```
</details>



## bugtracker.getBugreportSectionList

Неизвестно зачем нужен

### Параметры

| Параметр     | Тип    | Описание               |
|--------------|--------|------------------------|
| bugreport_id | int    | ID репорта             |
| section      | string | `clones` или `similar` |



## bugtracker.getBugreportStatusBox

Получить данные для блока, через который нужно менять статус отчёта.

### Параметры

| Параметры    | Тип    | Описание                                |
|--------------|--------|-----------------------------------------|
| bugreport_id | int    | ID репорта                              |
| hash         | string | `change_status_hash` из объекта репорта |

### Тип возвращаемого значения

```ts

```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "current_status": 5,
    "suggested_status": 5,
    "statuses": [
      {
        "id": 5,
        "name": "Закрыт"
      },
      {
        "id": 7,
        "name": "Переоткрыт"
      }
    ],
    "status_comment_required": [
      7
    ]
  }
  ```
</details>



## bugtracker.getComments

Получить комментарии к репорту.

### Параметры

| Параметр     | Тип | Описание                              |
|--------------|-----|---------------------------------------|
| bugreport_id | int | ID репорта                            |
| count        | int | Количество комментариев. Максимум 100 |

### Тип возвращаемого значения

```ts

```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
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
  ```
</details>



## bugtracker.getDownloadVersionUrl

Получить адрес для загрузки версии.

### Параметр

| Параметр   | Тип    | Описание                          |
|------------|--------|-----------------------------------|
| product_id | int    | ID продукта                       |
| version_id | int    | ID версии                         |
| hash       | string | `download_hash` из объекта версии |

### Тип возвращаемого значения

```ts

```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "url": "https://vk.link/to/version.apk",
    "app_title": "VK для Android",
    "bundle_name": "com.vkontakte.android",
    "build_id": 1234,
    "build_title": "1.0"
  }
  ```
</details>



## bugtracker.getEditDeviceFormData

Список ОС

### Тип возвращаемого значения

```ts

```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "platforms": [
      {
        "id": 0,
        "name": "Другая",
        "versions": []
      },
      {
        "id": 1,
        "name": "Windows",
        "versions": [
          {
            "id": 0,
            "name": "Другая"
          }
        ]
      },
      {
        "id": 2,
        "name": "MacOS",
        "versions": [
          {
            "id": 0,
            "name": "Другая"
          }
        ]
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
          },
          {
            "id": 0,
            "name": "Другая"
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
          },
          {
            "id": 0,
            "name": "Другая"
          }
        ]
      },
      {
        "id": 5,
        "name": "Linux",
        "versions": [
          {
            "id": 0,
            "name": "Другая"
          }
        ]
      }
    ]
  }
  ```
</details>



## bugtracker.getInfo

Получение информации о текущем пользователе. Не принимает параметров.

### Тип возвращаемого значения

```ts

```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "balance": 0,
    "updates_count": 0,
    "can_add_report": true,
    "can_search_reports": true,
    "can_view_products_list": true,
    "can_view_testers_list": true,
    "can_view_updates": true,
    "can_view_shop": true,
    "can_view_personal_page": true,
    "can_view_personal_settings": true,
    "can_view_authored_reports": true,
    "can_view_bookmarks": true
  }
  ```
</details>



## bugtracker.getProductBranches

Получить ветки продукта.

### Параметры

| Параметр   | Тип | Описание    |
|------------|-----|-------------|
| product_id | int | ID продукта |

### Тип возвращаемого значения

```ts

```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "count": 1,
    "items": [
      {
        "id": 1,
        "title": "Branch name",
        "description": "Branch description",
        "photo": "",
        "parent_product": {
          "id": 2,
          "title": "Parent product",
          "description": "Parent product description",
          "photo": ""
        },
        "reports_count": 1
      }
    ]
  }
  ```
</details>



## bugtracker.getProductVersions

Получить версии продукта.

### Параметры

| Параметр    | Тип | Описание                                        |
|-------------|-----|-------------------------------------------------|
| product_id  | int | ID продукта                                     |
| version_ids | int | ID версий                                       |
| count       | int | Количество версий                               |
| extended    | int | Флаг. Получить расширенную информацию о версиях |

### Тип возвращаемого значения

```ts

```

### Пример ответа

<details>
  <summary>extended = 0</summary>

  ```json
  {
    "items": [
      {
        "id": 1,
        "product_id": 1,
        "title": "Название версии",
        "release_notes": "Описание версии",
        "date": 1589025277,
        "reports_count": 146,
        "reports_url": "/bugs?product=1&version=1&status=100&wishes=1",
        "closed_reports_count": 0,
        "closed_reports_url": "/bugs?product=1&version=1&status=5&wishes=1",
        "vulnerability_reports_count": 0
      }
    ]
  }
  ```
</details>

<details>
  <summary>Открыть</summary>

  ```json
  {
    "items": [
      {
        "id": 1,
        "product_id": 1,
        "title": "Название версии",
        "release_notes": "Описание версии",
        "date": 1589025277,
        "reports_count": 146,
        "reports_url": "/bugs?product=1&version=1&status=100&wishes=1",
        "closed_reports_count": 0,
        "closed_reports_url": "/bugs?product=1&version=1&status=5&wishes=1",
        "vulnerability_reports_count": 0,
        "platform": 4,
        "download_hash": ""
      }
    ]
  }
  ```
</details>



## bugtracker.getProducts

Получить продукты.

### Параметры

| Параметр | Тип    | Описание                                |
|----------|--------|-----------------------------------------|
| section  | string | Секция: `all`, `my`, `download`         |
| count    | int    | Количество продуктов. Лимит возможно 20 |
| offset   | int    | Оффсет                                  |
| platform | int    | Неизвестно. Я видел `3`                 |
| q        | string | Строка поиска                           |

### Тип возвращаемого значения

```ts

```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "items": [
      {
        "id": 1,
        "title": "Product name",
        "description": "Description",
        "photo": "",
        "is_available": true,
        "reports_count": 1,
        "wishes_reports_count": 2
      }
    ],
    "sections": [
      {
        "id": "all"
      },
      {
        "id": "my",
        "products_count": 75
      },
      {
        "id": "download",
        "products_count": 3
      }
    ]
  }
  ```
</details>



## bugtracker.getProductsById

Получить продукты по ID.

### Параметры

| Параметр    | Тип    | Описание                                     |
|-------------|--------|----------------------------------------------|
| product_ids | string | ID продуктов через запятую                   |
| extended    | int    | Флаг. Вернуть расширенную информацию или нет |

### Тип возвращаемого значения

```ts

```

### Пример ответа

<details>
  <summary>extended = 0</summary>

  ```json
  {
    "items": [
      {
        "id": 1,
        "title": "Product",
        "description": "Description",
        "photo": "",
        "is_available": true,
        "reports_count": 5000,
        "wishes_reports_count": 1000
      }
    ]
  }
  ```
</details>

<details>
  <summary>extended = 1</summary>

  ```json
  {
    "items": [
      {
        "id": 1,
        "title": "Product",
        "description": "Description",
        "photo": "",
        "is_available": true,
        "counters": [
          {
            "type": "reporters_count",
            "count": 1000,
            "url": ""
          },
          {
            "type": "reports_count",
            "count": 5000,
            "url": "bugs?product=1&status=100"
          },
          {
            "type": "open_reports_count",
            "count": 500,
            "url": "bugs?product=1&status=0"
          },
          {
            "type": "in_progress_reports_count",
            "count": 3500,
            "url": "bugs?product=1&status=4,1"
          },
          {
            "type": "closed_reports_count",
            "count": 1500,
            "url": "bugs?product=1&status=2,5"
          }
        ],
        "reports_count": 5000,
        "wishes_reports_count": 1000,
        "open_reports_count": 50,
        "in_progress_reports_count": 3500,
        "closed_reports_count": 1500,
        "members_count": 1000,
        "can_add_report": true,
        "can_view_versions": true,
        "leave_hash": "",
        "leave_button": "Выйти из тестирования",
        "note": "Версия 1.0 (1111)",
        "status_note": "",
        "licence_status": 3,
        "is_licence_ok": true,
        "is_notify_enabled": true,
        "set_notify_hash": "",
        "can_view_branches": true
      }
    ]
  }
  ```
</details>

<details>
  <summary>Продукт, к которому можно присоединиться</summary>

  ```json
  {
    "id": 2,
    "title": "Product",
    "description": "Description",
    "photo": "",
    "join_hash": "",
    "join_button": "Присоединиться",
    "note": "",
    "status_note": "Вы отказались от участия в тестировании",
    "licence_status": 5
  }
  ```
</details>



## bugtracker.getProductVersions

Получить версии продукта.

### Параметры

| Параметр    | Тип | Описание                                        |
|-------------|-----|-------------------------------------------------|
| product_id  | int | ID продукта                                     |
| version_ids | int | ID версий                                       |
| count       | int | Количество версий                               |
| extended    | int | Флаг. Получить расширенную информацию о версиях |

### Тип возвращаемого значения

```ts

```

### Пример ответа

<details>
  <summary>extended = 0</summary>

  ```json
  {
    "items": [
      {
        "id": 1,
        "product_id": 1,
        "title": "Название версии",
        "release_notes": "Описание версии",
        "date": 1589025277,
        "reports_count": 146,
        "reports_url": "/bugs?product=1&version=1&status=100&wishes=1",
        "closed_reports_count": 0,
        "closed_reports_url": "/bugs?product=1&version=1&status=5&wishes=1",
        "vulnerability_reports_count": 0
      }
    ]
  }
  ```
</details>

<details>
  <summary>extended = 1</summary>

  ```json
  {
    "items": [
      {
        "id": 1,
        "product_id": 1,
        "title": "Название версии",
        "release_notes": "Описание версии",
        "date": 1589025277,
        "reports_count": 146,
        "reports_url": "/bugs?product=1&version=1&status=100&wishes=1",
        "closed_reports_count": 0,
        "closed_reports_url": "/bugs?product=1&version=1&status=5&wishes=1",
        "vulnerability_reports_count": 0,
        "platform": 4,
        "download_hash": ""
      }
    ]
  }
  ```
</details>



## bugtracker.getReporterProducts

Метод возвращает список продуктов пользователя

### Параметры

| Параметр    | Тип | Описание                                                                 |
|-------------|-----|--------------------------------------------------------------------------|
| reporter_id | int | ID пользователя. Необязательный                                          |
| preview     | int | Флаг. Если `1`, то в ответе будут три рандомных продукта. Необязательный |

### Тип возвращаемого значения

```ts

```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "items": [
      {
        "id": 1,
        "title": "Product",
        "description": "Description",
        "photo": "",
        "is_available": true,
        "user_reports_count": 1,
        "reports_count": 1000,
        "wishes_reports_count": 250
      }
    ],
    "available_products_count": 75,
    "secret_products_count": 0,
    "secret_reports_count": 0,
    "uncounted_reports_count": 0,
    "unshown_reports_count": 150
  }
  ```
</details>



## bugtracker.getReportersById

Получить карточки тестировщиков.

### Параметры

| Параметр     | Тип    | Значение                                                            |
|--------------|--------|---------------------------------------------------------------------|
| reporter_ids | string | Числовые ID пользователей через запятую. Максимум 100 пользователей |
| fields       | string | https://vk.com/dev/objects/user                                     |
| extended     | int    | Флаг. Если `1`, то будет возвращена сетка активности                |

### Тип возвращаемого значения

```ts

```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "items": [
      {
        "id": 1,
        "status_text": "Не участвует в программе VK Testers",
        "reports_count": 0,
        "top_position": 0
      },
      {
        "id": 305360617,
        "status_text": "#129 в общем рейтинге, 168 отчётов",
        "reports_count": 168,
        "top_position": 129
      }
    ],
    "profiles": [
      {
        "id": 1,
        "first_name": "Павел",
        "last_name": "Дуров",
        "is_closed": false,
        "can_access_closed": true
      },
      {
        "id": 305360617,
        "first_name": "Матвей",
        "last_name": "Вишневский",
        "is_closed": false,
        "can_access_closed": true
      }
    ]
  }
  ```
</details>



## bugtracker.getReportersTop

Получить топ участников

### Параметры

| Параметр | Тип    | Описание                             |
|----------|--------|--------------------------------------|
| count    | int    | Количество участников. Минимум 10    |
| fields   | string | https://vk.com/dev/objects/user      |
| sort     | string | Тип сортировки: `rate` или `reports` |
| q        | string | Строка поиска                        |

### Тип возвращаемого значения

```ts

```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "items": [
      {
        "id": 1,
        "rating": 29000,
        "reports_count": 4000
      }
    ],
    "profiles": [
      {
        "id": 1,
        "first_name": "Имя",
        "last_name": "Фамилия",
        "is_closed": false,
        "can_access_closed": true
      }
    ]
  }
  ```
</details>



## bugtracker.getSearchParameters

Возвращает параметры для поиска. Типы, теги, все дела.

### Тип возвращаемого значения

```ts

```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "products": [
      {
        "id": 1,
        "name": "Product",
        "version": "1.0",
        "tags": [
          {
            "id": 5,
            "name": "Вложения"
          },
          {
            "id": 61,
            "name": "Дизайн"
          },
          {
            "id": 16,
            "name": "Другое"
          },
          {
            "id": 223,
            "name": "Магазин"
          },
          {
            "id": 14,
            "name": "Поиск"
          },
          {
            "id": 2,
            "name": "Профиль"
          },
          {
            "id": 8,
            "name": "Уведомления"
          },
          {
            "id": 107,
            "name": "Универсальный доступ"
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
        ],
        "requires_device": true,
        "can_search_wishes": true
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
    "originals": [
      {
        "id": 0,
        "name": "Все, кроме повторов"
      },
      {
        "id": 1,
        "name": "Все"
      },
      {
        "id": 2,
        "name": "Только с повторами"
      },
      {
        "id": 3,
        "name": "Только без повторов"
      },
      {
        "id": 4,
        "name": "Только повторы"
      }
    ],
    "statuses": [
      {
        "id": 0,
        "name": "Открыт"
      },
      {
        "id": 4,
        "name": "На рассмотрении"
      },
      {
        "id": 1,
        "name": "В работе"
      },
      {
        "id": 2,
        "name": "Исправлен"
      },
      {
        "id": 7,
        "name": "Переоткрыт"
      },
      {
        "id": 5,
        "name": "Закрыт"
      },
      {
        "id": 9,
        "name": "Отложен"
      },
      {
        "id": 6,
        "name": "Заблокирован"
      },
      {
        "id": 3,
        "name": "Отклонён"
      },
      {
        "id": 8,
        "name": "Не воспроизводится"
      },
      {
        "id": 10,
        "name": "Требует корректировки"
      },
      {
        "id": 99,
        "name": "Неактуальные"
      },
      {
        "id": 100,
        "name": "Любой статус"
      }
    ]
  }
  ```
</details>



## bugtracker.getSettings

Получить список устройств

### Тип возвращаемого значения

```ts

```

### Пример ответа

<details>
  <summary>Открыть</summary>

  `login_ha` — логин HockeyApp
  `login_tf` — логин TestFlight

  ```json
  {
    "login_ha": "ha***@slmatthew.dev",
    "login_tf": "",
    "devices": [
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
    "can_add_device": true
  }
  ```
</details>



## bugtracker.joinProduct

Присоединиться к продукту

### Параметры

| Параметр   | Тип    | Описание    |
|------------|--------|-------------|
| product_id | int    | ID продукта |
| hash       | string | `join_hash` |

### Тип возвращаемого значения

```ts

```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  1
  ```
</details>



## bugtracker.leaveProduct

Выйти из продукта

### Параметры

| Параметр   | Тип    | Описание     |
|------------|--------|--------------|
| product_id | int    | ID продукта  |
| hash       | string | `leave_hash` |

### Тип возвращаемого значения

```ts

```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  1
  ```
</details>



## bugtracker.removeBugreport

Удалить репорт

### Параметры

| Параметр     | Тип    | Описание      |
|--------------|--------|---------------|
| bugreport_id | int    | ID репорта    |
| hash         | string | `remove_hash` |

### Тип возвращаемого значения

```ts

```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  1
  ```
</details>



## bugtracker.reproduce

Поставить отметку «Воспроизводится» или «Нравится»

### Параметры

| Параметр     | Тип    | Описание                                    |
|--------------|--------|---------------------------------------------|
| bugreport_id | int    | ID репорт                                   |
| hash         | string | `bugreport.reproduces.reproduce_hash`       |
| state        | int    | 1 - воспроизводится, 0 - не воспроизводится |

### Тип возвращаемого значения

```ts

```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
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
  ```
</details>



## bugtracker.restoreComment

Восстановить комментарий.

### Параметры

| Параметр     | Тип    | Описание                                     |
|--------------|--------|----------------------------------------------|
| bugreport_id | int    | ID репорта                                   |
| comment_id   | int    | ID комментария                               |
| hash         | string | `restore_hash` из `bugtracker.deleteComment` |

### Тип возвращаемого значения

```ts

```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  1
  ```
</details>



## bugtracker.saveBugreport

Сохранить репорт

### Параметры

| Параметр           | Тип     | Описание                                           |
|--------------------|---------|----------------------------------------------------|
| bugreport_id       | int     | ID репорта. Если 0, то будет создан новый репорт   |
| product_id         | int     | ID продукта                                        |
| title              | string  | Заголовок                                          |
| description        | string  | Шаги воспроизведения                               |
| state_supposed     | string  | Ожидаемый результат                                |
| state_actual       | string  | Фактический результат                              |
| severity           | int     | Приоритет                                          |
| issue_type         | int     | Тип проблемы                                       |
| confidential       | int     | Флаг. Отвечает за скрытие документов               |
| attachments        | string  | Скорее всего, вложения в стиле `photo1_1,photo1_2` |
| tags               | string  | ID тегов через запятую                             |
| platforms          | string  | ID платформ через запятую                          |
| platforms_versions | string  | Версии платформ через запятую                      |
| user_devices       | string  | ID устройств через запятую                         |
| phone              | unknown | ?                                                  |
| hash               | string  | `hash` из `bugtracker.editBugreport`               |
| comment            | unknown | ?                                                  |

### Тип возвращаемого значения

```ts

```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "bugreport_id": 123
  }
  ```
</details>



## bugtracker.saveDevice

Видимо, нужен для сохранения нового устройства.

### Параметры

| Параметр    | Тип     | Описание                                   |
|-------------|---------|--------------------------------------------|
| hash        | string  | Возможно, `add_hash` из объекта устройства |
| brand       | string  | Наверное, компания-производитель           |
| device_name | string  | Название устройства                        |
| model       | string  | Модель устройства                          |
| platform    | unknown | Платформа                                  |



## bugtracker.saveUserDevice

Сохранить настройки устройства

### Параметры

| Параметр         | Тип    | Описание      |
|------------------|--------|---------------|
| user_device_id   | int    | ID устройства |
| hash             | string | `edit_hash`   |
| platform_version | int    | ID версии ОС  |

### Тип возвращаемого значения

```ts

```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  1
  ```
</details>



## bugtracker.searchBugreports

Получить репорты.

### Параметры

| Параметр    | Тип | Описания                               |
|-------------|-----|----------------------------------------|
| reporter_id | int | ID пользователя                        |
| count       | int | Количество отчетов                     |
| status      | int | Статус отчётов                         |
| start_from  | int | Оффсет. Можно использовать `next_from` |

#### Коды статусов
* Открыт `0`
* На рассмотрении `4`
* В работе `1`
* Исправлен `2`
* Переоткрыт `7`
* Закрыт `5`
* Отложен `9`
* Заблокирован `6`
* Отклонён `3`
* Не воспроизводится `8`
* Требует корректировки `10`
* Неактуальные `99`
* Любой статус `100`

### Тип возвращаемого значения

```ts

```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "count": 23321,
    "next_from": 1589053866,
    "items": [
      {
        "id": 1,
        "title": "Bugreport title",
        "owner_id": 351888705,
        "created": 1589053866,
        "updated": 1589053866,
        "status": {
          "id": 0,
          "name": "Открыт"
        },
        "comments_count": 1,
        "product": {
          "id": 1,
          "name": "Product"
        },
        "tags": [
          {
            "id": 108,
            "name": "Друзья"
          },
          {
            "id": 2,
            "name": "Профиль"
          }
        ],
        "reproduces": {
          "count": 0
        }
      }
    ],
    "profiles": [
      {
        "id": 351888705,
        "first_name": "Ян",
        "last_name": "Дроздов",
        "deactivated": "deleted"
      }
    ]
  }
  ```
</details>



## bugtracker.searchDevices

Ищет устройства или возвращает популярные устройства (если не указать `q`).

### Параметры

| Параметр | Тип    | Описание             |
|----------|--------|----------------------|
| q        | string | Строка поиска        |
| count    | int    | Количество устройств |

### Тип возвращаемого значения

```ts
interface BugtrackerSearchDevices {
  items: VKDevice
  save_device_hash: string
}

interface VKDevice {
  id: number
  status: 0
  title: string
  platform: {
    id: number
    name: 'Android' | 'iOS' | 'Windows' | 'MacOS' | 'Linux'
  }
  model?: string
  add_hash: string
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "items": [{
      "id": 20298,
      "status": 0,
      "title": "Linux Deepin",
      "platform": {
        "id": 5,
        "name": "Linux"
      },
      "model": "Acer",
      "add_hash": "..."
    }],
    "save_device_hash": "..."
  }
  ```
</details>



## bugtracker.setProductVersionNotify

Настроить уведомления о новых версиях

### Параметры

| Параметры  | Тип    | Описание                                              |
|------------|--------|-------------------------------------------------------|
| product_id | int    | ID продукта                                           |
| hash       | string | `set_notify_hash` из `getProductsById` с `extended=1` |

### Тип возвращаемого значения

```ts

```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "is_notify_enabled": false
  }
  ```
</details>



## bugtracker.updateBugreportVersion

Добавить отметку об актуальности отчета в новой версии продукта

### Параметры

| Параметр     | Тип    | Описание                               |
|--------------|--------|----------------------------------------|
| bugreport_id | int    | ID репорта                             |
| hash         | string | `bugreport.close_on_update.close_hash` |
| actual       | int    | Флаг. `1` - актуально                  |

### Тип возвращаемого значения

```ts

```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  1
  ```
</details>
