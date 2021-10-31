# bugtracker

Методы для работы с [баг-трекером](https://vk.com/bugs)

## Доступ

TODO

## Список методов

TODO



## bugtracker.addUserDevice

Добавляет устройство в карточку тестировщика.

### Параметры

| Параметр      | Тип    | Описание              |
|---------------|--------|-----------------------|
| **device_id** | int    | ID устройства         |
| **hash**      | string | `add_hash` устройства |

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
      "id": 21984,
      "status": 0,
      "title": "Apple iPhone 12",
      "platform": {
        "id": 3,
        "name": "iOS"
      },
      "model": "MGJA3RU\/A",
      "platform_version": {
        "id": 3,
        "name": "iOS 10"
      },
      "user_device_id": 483300000,
      "edit_hash": "...",
      "remove_hash": "..."
    }
  }
  ```
</details>

### Связанные методы

* bugtracker.searchDevices



## bugtracker.bookmark

Добавляет или удаляет отчёт из закладок.

### Параметры

| Параметр         | Тип    | Описание                          |
|------------------|--------|-----------------------------------|
| **bugreport_id** | int    | ID отчёта                         |
| **hash**         | string | `bookmark_hash` из объекта отчёта |

### Тип возвращаемого значения

```ts
interface BugtrackerBookmark {
  is_bookmarked: boolean
  subscribe_state: {
    can_set_subscribe: boolean
  }
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "is_bookmarked": false,
    "subscribe_state": {
      "can_set_subscribe": false
    }
  }
  ```
</details>



## bugtracker.changeBugreportStatus

Изменяет статус отчёта.

### Параметры

| Параметр         | Тип    | Описание                               |
|------------------|--------|----------------------------------------|
| **bugreport_id** | int    | ID отчёта                              |
| **hash**         | string | `change_status_hash` из объекта отчёта |
| status           | int    | ID нового статуса отчёта               |
| comment          | string | Текст комментария                      |

Если не указывать `status` или если значение этого поля будет совпадать с установленным статусом, будет возвращен `0`.

### Тип возвращаемого значения

```ts
type BugtrackerChangeBugreportStatus = 0 | 1;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  1
  ```
</details>



## bugtracker.createComment

Добавляет комментарий к отчёту.

### Параметры

| Параметр         | Тип           | Описание          |
|------------------|---------------|-------------------|
| **bugreport_id** | int           | ID отчёта         |
| **text**         | string        | Текст комментария |
| hash             | string        | ???               |
| attachments      | array[string] | Вложения          |

### Тип возвращаемого значения

```ts
interface BugtrackerCreateComment {
  comment: VKBugtrackerComment
  comment_flood: boolean
  subscribe_state: {
    can_set_subscribe: boolean
  }
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "comment": {
      "bugreport_id": 123456,
      "comment_id": 4,
      "created": 1635624195,
      "text": "just a test",
      "from_id": 305360617,
      "author_name": "Матвей Саловский",
      "author_photo": "",
      "edit_hash": "...",
      "remove_hash": "..."
    },
    "comment_flood": false,
    "subscribe_state": {
      "can_set_subscribe": false
    }
  }
  ```
</details>

### Связанные методы

* bugtracker.deleteComment
* bugtracker.editComment



## bugtracker.deleteComment

Удаляет комментарий к отчёту.

### Параметры

| Параметр         | Тип    | Описание                             |
|------------------|--------|--------------------------------------|
| **bugreport_id** | int    | ID отчёта                            |
| **comment_id**   | int    | ID комментария                       |
| **hash**         | string | `remove_hash` из объекта комментария |

### Тип возвращаемого значения

```ts
interface BugtrackerDeleteComment {
  restore_hash: string
  subscribe_state: {
    can_set_subscribe: boolean
  }
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "restore_hash": "...",
    "subscribe_state": {
      "can_set_subscribe": false
    }
  }
  ```
</details>

### Связанные методы

* bugtracker.restoreComment



## bugtracker.deleteUserDevice

Удаляет устройство из профиля тестировщика.

### Параметры

| Параметр           | Тип    | Описание                            |
|--------------------|--------|-------------------------------------|
| **user_device_id** | int    | ID устройства                       |
| **hash**           | string | `remove_hash` из объекта устройства |

### Тип возвращаемого значения

```ts
interface BugtrackerDeleteUserDevice {
  can_add_device: boolean
  platform_ids: int[] // ID платформ, для которых остались добавленные устройства
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "can_add_device": true,
    "platform_ids": [
      1,
      4,
      3
    ]
  }
  ```
</details>



## bugtracker.editComment

Редактирует комментарий к отчёту.

### Параметры

| Параметры        | Тип           | Описание                             |
|------------------|---------------|--------------------------------------|
| **bugreport_id** | int           | ID отчёта                            |
| **text**         | string        | Текст отредактированного комментария |
| **comment_id**   | int           | ID комментария                       |
| **hash**         | string        | `edit_hash` из объекта комментария   |
| attachments      | array[string] | Вложения                             |

> Чтобы убрать вложения из комментария, оставьте поле `attachments` пустым.

### Тип возвращаемого значения

```ts
interface BugtrackerEditComment {
  comment: VKBugtrackerComment
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "comment": {
      "bugreport_id": 123456,
      "comment_id": 4,
      "created": 1635624195,
      "text": "just a test 2",
      "from_id": 305360617,
      "author_name": "Матвей Саловский",
      "author_photo": "",
      "edit_hash": "...",
      "remove_hash": "..."
    }
  }
  ```
</details>

### Связанные методы

* bugtracker.createComment
* bugtracker.deleteComment



## bugtracker.getComments

Возвращает комментарии к отчёту.

### Параметры

| Параметр         | Тип | Описание                                |
|------------------|-----|-----------------------------------------|
| **bugreport_id** | int | ID отчёта                               |
| count            | int | Количество комментариев. Максимум `100` |

### Тип возвращаемого значения

```ts
interface BugtrackerGetComments {
  count: number
  items: {
    bugreport_id: number
    comment_id: number
    created: number
    text: string
    meta_text?: string
    from_id?: number
    author_name: string
    author_photo: string
  }[]
  comment_hash: string
  comment_flood: boolean
  can_add_hidden_comment: boolean
  can_add_moder_comment: boolean
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "count": 2,
    "items": [{
      "bugreport_id": 123456,
      "comment_id": 1,
      "created": 1559760889,
      "text": "йоу йоу йоу",
      "from_id": 305360617,
      "author_name": "Матвей Саловский",
      "author_photo": ""
    }, {
      "bugreport_id": 123456,
      "comment_id": 2,
      "created": 1559834261,
      "text": "",
      "meta_text": "Новый статус отчёта – <b>На рассмотрении<\/b>",
      "author_name": "Модератор",
      "author_photo": ""
    }],
    "comment_hash": "...",
    "comment_flood": false,
    "can_add_hidden_comment": false,
    "can_add_moder_comment": false
  }
  ```
</details>



## bugtracker.getEditDeviceFormData

Возвращает список ОС и их версий для редактирования информации об устройстве.

### Тип возвращаемого значения

<!-- надо будет переделать --->

```ts
interface SimpleItem {
  id: number
  name: string
}

interface VKPlatform {
  id: number
  name: string
  versions: SimpleItem[]
}

interface BugtrackerGetEditDeviceFormData {
  platforms: VKPlatform[]
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "platforms": [{
      "id": 0,
      "name": "Другая",
      "versions": []
    },
    {
      "id": 1,
      "name": "Windows",
      "versions": [{
        "id": 0,
        "name": "Другая"
      }]
    },
    {
      "id": 3,
      "name": "iOS",
      "versions": [{
        "id": 8,
        "name": "iOS 15"
      }, {
        "id": 7,
        "name": "iOS 14"
      }]
    }]
  }
  ```
</details>



## bugtracker.getSettings

Возвращает настройки профиля тестировщика.

### Тип возвращаемого значения

```ts
interface BugtrackerGetSettings {
  login_tf: string // логин в TestFlight
  devices: VKDevice[]
  can_add_device: boolean
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "login_tf": "tf***@slmatthew.dev",
    "devices": [{
      "id": 20321,
      "status": 0,
      "title": "Apple iPhone 11",
      "platform": {
          "id": 3,
          "name": "iOS"
      },
      "platform_version": {
          "id": 8,
          "name": "iOS 15"
      },
      "user_device_id": 48330000,
      "edit_hash": "...",
      "remove_hash": "..."
    }],
    "can_add_device": true
  }
  ```
</details>



## bugtracker.restoreComment

Восстанавливает удалённый комментарий к отчёту.

### Параметры

| Параметр         | Тип    | Описание                                              |
|------------------|--------|-------------------------------------------------------|
| **bugreport_id** | int    | ID отчёта                                             |
| **comment_id**   | int    | ID комментария                                        |
| **hash**         | string | `restore_hash`, возвращаемый bugtracker.deleteComment |

### Тип возвращаемого значения

```ts
type BugtrackerRestoreComment = 1;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  1
  ```
</details>

### Связанные методы

* bugtracker.createComment
* bugtracker.deleteComment
* bugtracker.editComment



## bugtracker.saveUserDevice

Редактирует версию ОС устройства, добавленного в профиль тестировщика.

### Параметры

| Параметр             | Тип    | Описание                          |
|----------------------|--------|-----------------------------------|
| **user_device_id**   | int    | ID устройства                     |
| **hash**             | string | `edit_hash` из объекта устройства |
| **platform_version** | int    | ID версии ОС                      |

### Тип возвращаемого значения

```ts
type BugtrackerSaveUserDevice = 1;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  1
  ```
</details>



## bugtracker.searchDevices

Осуществляет поиск устройств по заданной подстроке.

### Параметры

| Параметр | Тип    | Описание                         |
|----------|--------|----------------------------------|
| q        | string | Строка поиска                    |
| count    | int    | Количество возвращаемых значений |

Если не указан параметр `q`, то метод вернет самые популярные устройства.

### Тип возвращаемого значения

```ts
interface BugtrackerSearchDevices {
  items: VKDevice[]
  save_device_hash: string
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "items": [{
      "id": 17318,
      "status": 0,
      "title": "Apple iPhone 7",
      "platform": {
          "id": 3,
          "name": "iOS"
      },
      "add_hash": "..."
    },
    {
      "id": 17344,
      "status": 0,
      "title": "Apple IPhone SE",
      "platform": {
          "id": 3,
          "name": "iOS"
      },
      "model": "SE",
      "add_hash": "..."
    }],
    "save_device_hash": "..."
  }
  ```
</details>
