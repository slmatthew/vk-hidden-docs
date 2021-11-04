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



## bugtracker.getAchievementById

Возвращает информацию о достижении.

### Параметры

| Параметр           | Тип    | Описание                                |
|--------------------|--------|-----------------------------------------|
| **achievement_id** | int    | ID достижения                           |
| from_id            | int    | todo                                    |
| extended           | int    | Укажите `1`, чтобы метод вернул профили |
| fields             | string | https://vk.com/dev/objects/user         |

### Тип возвращаемого значения

```ts
interface BugtrackerGetAchievementById {
  achievement: {
    id: number
    title: string
    description: string
    score: number
    photo_url: string
    status_self: {
      text: string
      date?: number
    }
    owner_ids?: int[]
  }
  profiles?: VKUser[]
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "achievement": {
      "id": 12,
      "title": "Элементарно!",
      "description": "Отчёт об уязвимости получает положительный статус",
      "score": 20,
      "photo_url": "",
      "status_self": {
        "text": "Вы получили это достижение {date}",
        "date": 1630538618
      },
      "owner_ids": [
        1,
        100,
        101
      ]
    }
  }
  ```
</details>



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



## bugtracker.getInfo

Возвращает информацию о текущем пользователем.

### Тип возвращаемого значения

```ts
interface BugtrackerGetInfo {
  balance: number
  updates_count: number
  can_add_report: boolean
  can_search_reports: boolean
  can_view_products_list: boolean
  can_view_testers_list: boolean
  can_view_updates: boolean
  can_view_shop: boolean
  can_view_personal_page: boolean
  can_view_personal_settings: boolean
  can_view_authored_reports: boolean
  can_view_bookmarks: boolean
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "balance": 53,
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

Возвращает ветки продукта.

### Параметры

| Параметр       | Тип | Описание    |
|----------------|-----|-------------|
| **product_id** | int | ID продукта |

### Тип возвращаемого значения

```ts
interface VKParentProduct {
  id: number
  title: string
  description: string
  photo: string
  is_over: boolean
}

interface BugtrackerGetProductBranches {
  count: number
  items: {
    id: number
    title: string
    description: string
    photo: string
    is_over: boolean
    parent_product: VKParentProduct
    reports_count: number
  }[]
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "count": 1,
    "items": [{
      "id": 2,
      "title": "название",
      "description": "описание",
      "photo": "",
      "is_over": false,
      "parent_product": {
        "id": 1,
        "title": "название",
        "description": "описание",
        "photo": "",
        "is_over": false
      },
      "reports_count": 1234
    }]
  }
  ```
</details>



## bugtracker.getProducts

Возвращает список продуктов.

### Параметры

| Параметр    | Тип    | Описание                        |
|-------------|--------|---------------------------------|
| **section** | string | Секция: `all`, `my`, `download` |
| platform    | int    | ID платформы                    |
| q           | string | Строка поиска                   |
| count       | int    | Количество продуктов            |
| offset      | int    | Смещение                        |

Параметр `platform` обладает очень странной логикой. Если указать `0` или `4` *(возможно есть и другие)*, в `response.sections` появится секция `download`:

```json
{
  "sections": [{
    "id": "all"
  }, {
    "id": "my",
    "products_count": 78
  }, {
    "id": "download",
    "products_count": 2
  }]
}
```

Если указать иное значение `platform`, то будет возвращены две секции:

```json
{
  "sections": [{
    "id": "all"
  }, {
    "id": "my",
    "products_count": 78
  }]
}
```

Такое поведение может быть связано с тем, что вкладка `Скачать` (`download`) доступна только в МБТ для Android.

### Тип возвращаемого значения

```ts
interface VKParentProduct {
  id: number
  title: string
  description: string
  photo: string
  is_over: boolean
}

interface BugtrackerGetProducts {
  items: {
    id: number
    title: string
    description: string
    photo: string
    is_available: boolean
    is_over: boolean
    parent_product?: VKParentProduct
    reports_count: number
    wishes_reports_count: number
  }[]
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "items": [{
      "id": 2,
      "title": "дочерний продукт",
      "description": "описание",
      "photo": "",
      "is_available": true,
      "is_over": false,
      "parent_product": {
        "id": 1,
        "title": "родительский продукт",
        "description": "описание",
        "photo": "",
        "is_over": false
      },
      "reports_count": 123,
      "wishes_reports_count": 12
    }, {
      "id": 1,
      "title": "родительский продукт",
      "description": "описание",
      "photo": "",
      "is_available": true,
      "is_over": false,
      "reports_count": 123,
      "wishes_reports_count": 12
    }],
    "sections": [{
      "id": "all"
    }, {
      "id": "my",
      "products_count": 78
    }]
  }
  ```
</details>



## bugtracker.getProductsById

Описание метода

### Параметры

| Параметр | Тип | Описание |
|----------|-----|----------|

Необязательные дополнения для параметров: более подробное описание, предупреждение или варианты использования

### Тип возвращаемого значения

```ts
interface BugtrackerGetProductsByIdSimple {
  id: number
  title: string
  description: string
  photo: string
  is_available: boolean
  is_over: boolean
  parent_product?: VKParentProduct
  reports_count?: number
  wishes_reports_count?: number
}

interface BugtrackerGetProductsByIdExtendedInProduct {
  id: number
  title: string
  description: string
  photo: string
  is_available: boolean
  is_over: boolean
  parent_product?: VKParentProduct
  counters: {
    type: string
    count: number
    url: string
  }[]
  reports_count: number
  wishes_reports_count: number
  open_reports_count: number
  in_progress_reports_count: number
  closed_reports_count: number
  members_count: number
  can_add_report: boolean
  can_view_versions: boolean
  leave_hash: string
  leave_button: 'Выйти из тестирования'
  note: string
  status_note: string // 'Вы отказались от участия в тестировании'
  licence_status: number
  is_licence_ok: boolean
  is_notify_enabled: boolean
  set_notify_hash: string
  can_view_branches?: boolean
}

// Возвращается, когда пользователь не вступил в продукт,
// вышел из него или когда заявка всё ещё рассматривается
interface BugtrackerGetProductsByIdExtendedNotInProduct {
  id: number
  title: string
  description: string
  photo: string
  is_available: boolean
  is_over: boolean
  parent_product?: VKParentProduct
  can_view_versions?: boolean
  // Только когда заявка в продукт ещё рассматривается
  leave_hash?: string
  leave_button?: 'Отменить заявку'
  // Поля join_ отсутствуют, если тестирование продукта завершено
  join_hash?: string
  join_button?: 'Присоединиться'
  note: string
  status_note: string // 'Вы отказались от участия в тестировании'
  licence_status?: number
  is_licence_ok?: boolean
  app_id?: number
}
```

### Пример ответа

<!-- пиздец надо будет тоже пересмотреть это говно --->

<details>
  <summary>Пользователь в продукте, extended = 0</summary>

  Типизация: `BugtrackerGetProductsByIdSimple`

  ```json
  {
    "items": [{
      "id": 1,
      "title": "название",
      "description": "описание",
      "photo": "",
      "is_available": true,
      "is_over": false,
      "reports_count": 12345,
      "wishes_reports_count": 1234
    }]
  }
  ```
</details>

<details>
  <summary>Пользователь в продукте, extended = 1</summary>

  Типизация: `BugtrackerGetProductsByIdExtendedInProduct`

  ```json
  {
    "items": [{
      "id": 1,
      "title": "название",
      "description": "описание",
      "photo": "",
      "is_available": true,
      "is_over": false,
      "counters": [{
        "type": "reporters_count",
        "count": 1234,
        "url": ""
      }, {
        "type": "reports_count",
        "count": 12345,
        "url": "bugs?act=reports&product=1&status=100"
      }, {
        "type": "open_reports_count",
        "count": 12,
        "url": "bugs?act=reports&product=1&status=0,7"
      }, {
        "type": "in_progress_reports_count",
        "count": 1234,
        "url": "bugs?act=reports&product=1&status=1,4,2"
      }, {
        "type": "closed_reports_count",
        "count": 12345,
        "url": "bugs?act=reports&product=1&status=2,11,12,5"
      }],
      "reports_count": 12345,
      "wishes_reports_count": 1234,
      "open_reports_count": 12,
      "in_progress_reports_count": 1234,
      "closed_reports_count": 12345,
      "members_count": 1234,
      "can_add_report": true,
      "can_view_versions": true,
      "leave_hash": "...",
      "leave_button": "Выйти из тестирования",
      "note": "Версия ...",
      "status_note": "",
      "licence_status": 3,
      "is_licence_ok": true,
      "is_notify_enabled": true,
      "set_notify_hash": "...",
      "can_view_branches": true
    }]
  }
  ```
</details>

<details>
  <summary>К продукту можно присоединиться или пользователь вышел из продукта, extended = 0</summary>

  Типизация: `BugtrackerGetProductsByIdSimple`

  ```json
  {
    "items": [{
      "id": 2,
      "title": "название",
      "description": "описание",
      "photo": "",
      "is_available": false,
      "is_over": false
    }]
  }
  ```
</details>

<details>
  <summary>К продукту можно присоединиться, extended = 1</summary>

  Типизация: `BugtrackerGetProductsByIdExtendedNotInProduct`

  ```json
  {
    "items": [{
      "id": 2,
      "title": "название",
      "description": "описание",
      "photo": "",
      "is_available": false,
      "is_over": false,
      "join_hash": "...",
      "join_button": "Присоединиться",
      "note": "",
      "status_note": "",
      "app_id": 1234567
    }]
  }
  ```
</details>

<details>
  <summary>Пользователь вышел из продукта, extended = 1</summary>

  Типизация: `BugtrackerGetProductsByIdExtendedNotInProduct`

  ```json
  {
    "items": [{
      "id": 3,
      "title": "название",
      "description": "описание",
      "photo": "описание",
      "is_available": false,
      "is_over": false,
      "join_hash": "...",
      "join_button": "Присоединиться",
      "note": "",
      "status_note": "Вы отказались от участия в тестировании",
      "licence_status": 5,
      "is_licence_ok": false,
      "app_id": 1234567
    }]
  }
  ```
</details>



## bugtracker.getProductVersions

Возвращает информацию о версиях продукта.

### Параметры

| Параметр       | Тип  | Описание                             |
|----------------|------|--------------------------------------|
| **product_id** | int  | ID продукта                          |
| count          | int  | Количество возвращаемых значений     |
| offset         | int  | Смещение                             |
| extended       | flag | Возвращать дополнительную информацию |

Поле `extended` предназначено для получения `download_hash`, необходимого при скачивании прикрепленного к версии файла.

### Тип возвращаемого значения

```ts
interface BugtrackerGetProductVersions {
  items: {
    id: number
    product_id: number
    title: string
    release_notes: string
    date: number
    reports_count: number
    reports_url: string
    closed_reports_count: number
    closed_reports_url: string
    vulnerability_reports_count: number
    is_hidden: boolean
    platform?: number // только при extended = 1; наблюдал только 4
    download_hash?: string // только при extended = 1
  }[]
}
```

### Пример ответа

<details>
  <summary>Ответ при extended = 0</summary>

  ```json
  {
    "items": [{
      "id": 1,
      "product_id": 1,
      "title": "версия 1",
      "release_notes": "описание версии",
      "date": 1635523223,
      "reports_count": 70,
      "reports_url": "\/bugs?act=reports&product=1&version=1&status=100",
      "closed_reports_count": 0,
      "closed_reports_url": "\/bugs?act=reports&product=1&version=1&status=5",
      "vulnerability_reports_count": 0,
      "is_hidden": false
    }]
  }
  ```
</details>

<details>
  <summary>Ответ при extended = 1</summary>

  ```json
  {
    "items": [{
      "id": 1,
      "product_id": 1,
      "title": "версия 1",
      "release_notes": "описание версии",
      "date": 1635523223,
      "reports_count": 70,
      "reports_url": "\/bugs?act=reports&product=1&version=1&status=100",
      "closed_reports_count": 0,
      "closed_reports_url": "\/bugs?act=reports&product=1&version=1&status=5",
      "vulnerability_reports_count": 0,
      "is_hidden": false,
      "platform": 4,
      "download_hash": "..."
    }]
  }
  ```
</details>



## bugtracker.getReporterProducts

Возвращает продукты, в которых состоит тестировщик.

### Параметры

| Параметр    | Тип  | Описание                                      |
|-------------|------|-----------------------------------------------|
| reporter_id | int  | ID пользователя                               |
| preview     | flag | Укажите `1` для получения сокращённого списка |

Если не указать `reporter_id`, будут возвращены продукты текущего пользователя.

Если `preview = 1`, то метод вернёт 3 случайных продукта, в которых состоит пользователь.

### Тип возвращаемого значения

```ts
interface VKParentProduct {
  id: number
  title: string
  description: string
  photo: string
  is_over: boolean
}

interface BugtrackerGetReporterProducts {
  items: {
    id: number
    title: string
    description: string
    photo: string
    is_available: boolean
    user_reports_count: number
    is_over: boolean
    parent_product?: VKParentProduct
    reports_count: number
    wishes_reports_count: number
  }[]
  available_products_count: number
  secret_products_count: number
  secret_reports_count: number
  uncounted_reports_count: number
  unshown_reports_count: number
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "items": [{
      "id": 1,
      "title": "название",
      "description": "описание",
      "photo": "",
      "is_available": true,
      "user_reports_count": 0,
      "is_over": false,
      "reports_count": 338,
      "wishes_reports_count": 47
    }],
    // Всего продуктов
    "available_products_count": 5,
    // В карточке тестировщика secret_products отображаются как '4 секретных продукта'
    "secret_products_count": 4,
    // В карточке тестировщика secret_reports отображаются как '6 отчётов скрыто'
    "secret_reports_count": 0,
    "uncounted_reports_count": 0,
    "unshown_reports_count": 0
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



## bugtracker.joinProduct

Позволяет вступить или вернуться в тестирование продукта.

### Параметры

| Параметр       | Тип    | Описание                        |
|----------------|--------|---------------------------------|
| **product_id** | int    | ID продукта                     |
| **hash**       | string | `join_hash` из объекта продукта |

### Тип возвращаемого значения

```ts
type BugtrackerJoinProduct = 1;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  1
  ```
</details>



## bugtracker.leaveProduct

Описание метода

### Параметры

| Параметр       | Тип    | Описание                         |
|----------------|--------|----------------------------------|
| **product_id** | int    | ID продукта                      |
| **hash**       | string | `leave_hash` из объекта продукта |

### Тип возвращаемого значения

```ts
type BugtrackerLeaveProduct = 1;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  1
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



## bugtracker.setProductVersionNotify

Включает или выключает оповещения о новых версиях продукта.

### Параметры

| Параметр       | Тип    | Описание                                    |
|----------------|--------|---------------------------------------------|
| **product_id** | int    | ID продукта                                 |
| **hash**       | string | `set_notify_hash` из объекта продукта       |
| notify         | flag   | `1` - включить уведомления, `0` - выключить |

Если не указать параметр `notify`, метод из сеттера превратится в геттер.

### Тип возвращаемого значения

```ts
interface BugtrackerSetProductVersionNotify {
  is_notify_enabled: boolean
}
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