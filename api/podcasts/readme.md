# podcasts

Методы для работы с подкастами.

Подкасты - это те же аудиозаписи, но с дополнительной метадатой.

## Доступ

Большинство методов из данной секции будут работать только с токеном от мини-приложения "Подкасты".

Для получения токена нужно открыть ссылку `https://oauth.vk.com/authorize?client_id=6756455&redirect_uri=https://oauth.vk.com/blank.html&display=page&response_type=token` и скопировать токен.

ID приложения (релиз): `6756455`

ID приложения (бета): `6828929`

## Список методов

* [podcasts.getStartPage](#podcastsgetstartpage) — получить главную страницу подкастов
* [podcasts.search](#podcastssearch) — поиск по каталогу подкастов
* [podcasts.clearRecentSearches](#podcastsclearrecentsearches) — очистка истории поиска подкастов
* [podcasts.getRandomEpisode](#podcastsgetrandomepisode) — получить случайный эпизод случайного подкаста
* [podcasts.markAsListened](#podcastsmarkaslistened) — уведомить о прослушанном эпизоде
* [podcasts.getFeed](#podcastsgetfeed) — получить прослушанные/в процессе прослушивания подкасты в формате ленты


## podcasts.search

Возвращает результаты поиска по каталогу подкастов.

### Параметры

| Параметр         | Тип    | Описание         |
|------------------|--------|------------------|
| **query_string** | string | Поисковый запрос |

### Тип возвращаемого значения

```ts
interface PodcastsSearch {
  podcasts: VKPodcastMeta[]
  episodes: VKAudio[]
  profiles: VKUser[]
  groups: VKGroup[]
}

interface VKPodcastMeta {
  owner_id: number,
  podcast_title: string
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
{
  "podcasts": [{
      "owner_id": -114035565,
      "podcast_title": "Zavtracast"
  }],
  "episodes": [{
      "artist": "Zavtracast",
      "id": 456239071,
      "owner_id": -114035565,
      "title": "Zavtracast Special  - Вопросы и Ответы: летняя версия",
      "duration": 3623,
      "is_explicit": false,
      "is_focus_track": false,
      "url": "...",
      "date": 1536848792,
      "lyrics_id": 430797219,
      "no_search": 1,
      "podcast_info": {
        "cover": {
          "sizes": [
            {
              "height": 807,
              "url": "...",
              "type": "a",
              "width": 807
            }
          ]
        },
        "description": "Привет, наши дорогие слуша...",
        "is_favorite": false,
        "plays": 5,
        "position": 0
      },
      "short_videos_allowed": false,
      "stories_allowed": false
  }],
  "profiles": [],
  "groups": [{
      "id": 114035565,
      "name": "Zavtracast",
      "screen_name": "zavtracast",
      "is_closed": 0,
      "type": "page",
      "members_count": 10242,
      "photo_50": "https://sun1-97.userapi.com/c639223/v639223461/3959b/kT3AnekfIe4.jpg?ava=1",
      "photo_100": "https://sun1-30.userapi.com/c639223/v639223461/3959a/8u_BUbTIDls.jpg?ava=1",
      "photo_200": "https://sun1-98.userapi.com/c639223/v639223461/39599/HP1unvj0v2c.jpg?ava=1"
  }]
}
  ```
</details>



## podcasts.getStartPage

Главная страница мини-приложения "Подкасты". Возвращает главную страницу с рекомендациями, чартом и блоками.

### Параметры

| Параметр | Тип    | Описание                                       |
|----------|--------|------------------------------------------------|
| extended | number | Возвращать в ответе поля `profiles` и `groups` |
| fields   | string | Возрат полей профилей                          |

### Тип возвращаемого значения

```ts
interface PodcastsGetStartPage {
  order: string[]
  in_progress: VKAudio[]
  bookmarks: VKAudio[]
  articles: VKArticle[]
  static_how_to: boolean[]
  subscriptions: VKAudio[]
  chart: VKPodcastChart
  search_tooltip: VKTooltip
  categories_list: VKPodcastCategory[]
  recommended_episodes: VKAudio[]
  catalog: VKPodcastCatalogBlock[]
}

interface VKPodcastCatalogBlock {
  category: VKPodcastCategory
  items: VKPodcastMeta[]
}

interface VKPodcastCategory {
  id: number
  title: string
  cover: VKCover[]
}

interface VKCover {
  height: number
  width: number
  url: string
}

interface VKPodcastMeta {
  owner_id: number
  podcast_title: string
}

interface VKPodcastChart {
  chart: VKPodcastChartMeta[]
  items: VKAudio[]
}

interface VKPodcastChartMeta {
  episode: string
  position: number
  diff: number
}
```



## podcasts.clearRecentSearches

Очистка истории поиска подкастов.

### Тип возвращаемого значения

```ts
type PodcastsClearRecentSearches = 1;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  1
  ```
</details>



## podcasts.getRandomEpisode

Получение случайного эпизода случайного подкаста.

### Тип возвращаемого значения

```ts
type PodcastsGetRandomEpisode = VKAudio;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
{
  "artist": "theBatya",
  "id": 456242831,
  "owner_id": -36965584,
  "title": "3D-художников не хватает, нейросети нас не заменят, а универсального софта нет",
  "duration": 3057,
  "is_explicit": false,
  "is_focus_track": false,
  "url": "...",
  "date": 1595257408,
  "lyrics_id": 448775225,
  "no_search": 1,
  "podcast_info": {
    "cover": {
      "sizes": [{
          "height": 640,
          "url": "...",
          "type": "a",
          "width": 640
      }]
    },
    "description": "В гостях Юри...",
    "is_favorite": false,
    "plays": 81,
    "position": 0,
    "is_random": true
  },
  "short_videos_allowed": false,
  "stories_allowed": false
}
  ```
</details>



## podcasts.markAsListened

Уведомляет ВК, что эпизод прослушан.

### Параметры

| Параметр       | Тип    | Описание     |
|----------------|--------|--------------|
| **owner_id**   | number | ID владельца |
| **episode_id** | number | ID эпизода   |

### Тип возвращаемого значения

```ts
type PodcastsMarkAsListened = number;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  1
  ```
</details>



## podcasts.getFeed

Получение ленты подкастов с выбранным фильтром и количеством. 

### Параметры

| Параметр       | Тип    | Описание                                        |
|----------------|--------|-------------------------------------------------|
| **filter**     | string | Фильтр ленты                                    |
| **count**      | number | Количество подкастов                            |
| start_from     | string | Смещение (поле `next_from`)                     |
| extended       | number | Возвращать в ответе поля `profiles` и `groups`  |

#### Доступные фильтры

| Название        | Описание                    |
|-----------------|-----------------------------|
| **recent**      | Недавно прослушанное        |
| **in_progress** | В процессе воспроизведения  |

### Тип возвращаемого значения

```ts
interface PodcastsGetFeed {
  items: VKAudio[],
  next_from: string,
  profiles: VKUser[],
  groups: VKGroup[]
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
{
  "items": [{
    "artist": "Zavtracast",
    "id": 456239286,
    "owner_id": -114035565,
    "title": "Завтракаст №194 – There is no need to be upset",
    "duration": 11667,
    "is_explicit": false,
    "is_focus_track": false,
    "url": "...",
    "date": 1596134144,
    "lyrics_id": 448930449,
    "no_search": 1,
    "podcast_info": {
      "cover": {
        "sizes": [{
          "height": 807,
          "url": "...",
          "type": "a",
          "width": 807
        }]
      },
      "description": "Нет нужды расстр...",
      "is_favorite": false,
      "plays": 19,
      "position": 0
    },
    "short_videos_allowed": false,
    "stories_allowed": false
  }],
  "next_from": "...",
  "profiles": [],
  "groups": [{
    "id": 114035565,
    "name": "Zavtracast",
    "screen_name": "zavtracast",
    "is_closed": 0,
    "type": "page",
    "members_count": 10244,
    "photo_50": "https://sun1-97.userapi.com/c639223/v639223461/3959b/kT3AnekfIe4.jpg?ava=1",
    "photo_100": "https://sun1-30.userapi.com/c639223/v639223461/3959a/8u_BUbTIDls.jpg?ava=1",
    "photo_200": "https://sun1-98.userapi.com/c639223/v639223461/39599/HP1unvj0v2c.jpg?ava=1"
  }]
}
  ```
</details>