# textlives

Методы для работы с текстовыми репортажами

## Доступ

Для доступа к этим методам нужен токен от приложения `7512376` (Репортажи).

https://oauth.vk.com/authorize?client_id=7512376&scope=&redirect_uri=https://oauth.vk.com/blank.html&display=page&response_type=token&revoke=1

## Список методов

* [textlives.changeFollowState](#textliveschangefollowstate)
* [textlives.changeState](#textliveschangestate)
* [textlives.deletePost](#textlivesdeletepost)
* [textlives.getCounters](#textlivesgetcounters)
* [textlives.getPosts](#textlivesgetposts)
* [textlives.getTextlive](#textlivesgettextlive)
* [textlives.pinPost](#textlivespinpost)



## textlives.changeFollowState

Позволяет включить или выключить уведомления о новых записях.

### Параметры

| Параметр             | Тип  | Описание                                    |
|----------------------|------|---------------------------------------------|
| **textlive_id**      | int  | ID репортажа                                |
| **new_follow_state** | flag | `1` - включить уведомления, `0` - выключить |

### Тип возвращаемого значения

```ts
type TextlivesChangeFollowState = 1;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  1
  ```
</details>



## textlives.changeState

Позволяет изменить статус репортажа.

### Параметры

| Параметр        | Тип | Описание     |
|-----------------|-----|--------------|
| **textlive_id** | int | ID репортажа |
| **new_state**   | int | Новый статус |

На данный момент известны следующие статусы:

| Значение | Описание                                |
|----------|-----------------------------------------|
| 1        | Репортаж создан, но не запущен          |
| 2        | Репортаж запущен и доступен подписчикам |
| 3        | Репортаж завершен                       |
| 5        | Репортаж удалён                         |

### Тип возвращаемого значения

```ts
type TextlivesChangeState = 1;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  1
  ```
</details>



## textlives.deletePost

Удаляет запись из репортажа.

### Параметры

| Параметр        | Тип | Описание     |
|-----------------|-----|--------------|
| **textlive_id** | int | ID репортажа |
| **post_id**     | int | ID записи    |

### Тип возвращаемого значения

```ts
type TextlivesDeletePost = 1;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  1
  ```
</details>



## textlives.getCounters

Возвращает количество читателей.

### Параметры

| Параметр        | Тип | Описание     |
|-----------------|-----|--------------|
| **textlive_id** | int | ID репортажа |
<!--| post_ids        | int | ID записей   |-->

### Тип возвращаемого значения

```ts
interface TextlivesGetCounters {
  counters: []
  readers_count: number
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "counters": [],
    "readers_count": 492
  }
  ```
</details>



## textlives.getPosts

Возвращает список записей в репортаже.

### Параметры

| Параметр        | Тип | Описание     |
|-----------------|-----|--------------|
| **textlive_id** | int | ID репортажа |
<!-- target_post_id | unknown | хз зачем -->

### Тип возвращаемого значения

```ts
interface TextlivesGetPosts {
  next_target_post_id: number
  previous_target_post_id: number
  unread_count: number
  posts: {
    id: number
    owner_id: number
    textlive_id: number
    attachment: {
      type: 'photo' | 'video' | 'poll' | ''
      photo?: VKPhoto
      video?: VKVideo
      poll?: VKPoll
    }
    date: number
    author_id: number
    text: string
    is_liked: boolean
    counters: {
      post_id: number
      likes: number
      shares: number
      views: number
    }
    is_important: boolean
  }[]
  authors: {
    id: number
    name: string
    photo_url: string
  }[]
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "next_target_post_id": 0,
    "previous_target_post_id": 0,
    "unread_count": 0,
    "posts": [{
      "id": 1,
      "owner_id": -194700000,
      "textlive_id": 1,
      "attachment": {
        "type": ""
      },
      "date": 1635762782,
      "author_id": 305360617,
      "text": "ррима",
      "is_liked": false,
      "counters": {
        "post_id": 3,
        "likes": 0,
        "shares": 0,
        "views": 3
      },
      "is_important": false
    }, {
      "id": 2,
      "owner_id": -194700000,
      "textlive_id": 1,
      "attachment": {
        "type": ""
      },
      "date": 1635763814,
      "author_id": -194700000,
      "text": "ДАДАДАДА",
      "is_liked": false,
      "counters": {
        "post_id": 4,
        "likes": 0,
        "shares": 0,
        "views": 1
      },
      "is_important": false
    }],
    "authors": [{
      "id": 305360617,
      "name": "Олег Нечипоренко",
      "photo_url": ""
    }, {
      "id": -194700000,
      "name": "хардбасия",
      "photo_url": ""
    }]
  }
  ```
</details>



## textlives.getTextlive

Возвращает информацию о репортаже.

### Параметры

| Параметр        | Тип | Описание     |
|-----------------|-----|--------------|
| **textlive_id** | int | ID репортажа |
<!-- ad_data | unknown | хз зачем -->

### Тип возвращаемого значения

```ts
interface VKPhotoSizes {
  height: number
  url: string
  type: string
  width: number
}

interface TextlivesGetTextLive {
  textlive: {
    id: number
    title: string
    state: number
    readers_count: number
    owner_id: number
    owner_title: string
    is_admin: boolean
    display_authors: boolean
    end_date?: number
    cover_photo?: {
      album_id: number
      date: number
      id: number
      owner_id: number
      has_tags: boolean
      sizes: VKPhotoSizes[]
      text: string
      user_id: number // 100
    }
    owner_photo: {
      album_id: number // 0
      date: number // 0
      id: number // 0
      owner_id: number // 0
      has_tags: boolean
      sizes: VKPhotoSizes[]
      owner_is_verified: boolean
    }
  }
  follow_state: number
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "textlive": {
      "id": 1,
      "title": "репортаж",
      "state": 2,
      "readers_count": 1,
      "owner_id": -194700000,
      "owner_title": "хардбасия",
      "is_admin": true,
      "display_authors": true,
      "owner_photo": {
        "album_id": 0,
        "date": 0,
        "id": 0,
        "owner_id": 0,
        "has_tags": false,
        "sizes": [{
          "height": 50,
          "url": "",
          "type": "e",
          "width": 50
        }]
      },
      "owner_is_verified": false
    },
    "follow_state": 0
  }
  ```
</details>



## textlives.pinPost

Позволяет закрепить запись в репортаже.

### Параметры

| Параметр        | Тип | Описание     |
|-----------------|-----|--------------|
| **textlive_id** | int | ID репортажа |
| **post_id**     | int | ID записи    |

Чтобы открепить запись, передайте `post_id = 0`.

### Тип возвращаемого значения

```ts
type TextlivesPinPost = 1;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  1
  ```
</details>
