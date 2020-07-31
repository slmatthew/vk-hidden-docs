# podcasts

Методы для работы с подкастами.
Подкасты - это те же аудиофайлы, но с дополнительной метадатой.

## Доступ

Большинство методов из данной секции будут работать только с токеном от VKUI-приложения "Подкасты".
AppID Staging: **6828929**
AppID Production: **6756455**

## Список методов

* [podcasts.search](#podcastssearch) — поиск по каталогу
* [podcasts.getStartPage](#podcastsgetstartpage) — главная страница подкастов
* [podcasts.clearRecentSearches](#podcastsclearrecentsearches) — очистка истории поиска
* [podcasts.getRandomEpisode](#podcastsgetrandomepisode) — получить рандомный эпизод
* [podcasts.markAsListened](#podcastsmarkaslistened) — уведомить о прослушанном эпизоде



## podcasts.search

Поиск по каталогу подкастов.

### Параметры

| Параметр         | Тип    | Описание         |
|------------------|--------|------------------|
| **query_string** | string | Поисковый запрос |

### Тип возвращаемого значения

Возвращает список найденных подкастов и эпизодов.

```ts
interface VKPodcastMeta {
  owner_id: number,
  podcast_title: string
}

interface PodcastsSearch {
  podcasts: VKPodcastMeta[]
  episodes: VKAudio[]
  profiles: VKProfile[]
  groups: VKProfile[]
};
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
  "response": {
    "podcasts": [
      {
        "owner_id": -114035565,
        "podcast_title": "Zavtracast"
      }
    ],
    "episodes": [
      {
        "artist": "Zavtracast",
        "id": 456239071,
        "owner_id": -114035565,
        "title": "Zavtracast Special  - Вопросы и Ответы: летняя версия",
        "duration": 3623,
        "is_explicit": false,
        "is_focus_track": false,
        "url": "*URL*",
        "date": 1536848792,
        "lyrics_id": 430797219,
        "no_search": 1,
        "podcast_info": {
          "cover": {
            "sizes": [
              {
                "height": 807,
                "url": "https:\/\/sun9-47.userapi.com\/c850228\/v850228583\/2945b\/QMo2OhFElHc.jpg",
                "type": "a",
                "width": 807
              },
              {
                "height": 320,
                "url": "https:\/\/sun9-15.userapi.com\/c850228\/v850228583\/29460\/V88ztOpoDpY.jpg",
                "type": "c",
                "width": 320
              },
              {
                "height": 200,
                "url": "https:\/\/sun9-5.userapi.com\/c850228\/v850228583\/2945f\/U_5i34MqGjw.jpg",
                "type": "e",
                "width": 200
              },
              {
                "height": 320,
                "url": "https:\/\/sun9-15.userapi.com\/c850228\/v850228583\/29460\/V88ztOpoDpY.jpg",
                "type": "b",
                "width": 320
              },
              {
                "height": 130,
                "url": "https:\/\/sun9-69.userapi.com\/c850228\/v850228583\/29459\/cFyW287T9lg.jpg",
                "type": "d",
                "width": 130
              },
              {
                "height": 130,
                "url": "https:\/\/sun9-69.userapi.com\/c850228\/v850228583\/29459\/cFyW287T9lg.jpg",
                "type": "f",
                "width": 130
              },
              {
                "height": 75,
                "url": "https:\/\/sun9-62.userapi.com\/c850228\/v850228583\/29458\/yc8kU9Jdqls.jpg",
                "type": "h",
                "width": 75
              },
              {
                "height": 604,
                "url": "https:\/\/sun9-30.userapi.com\/c850228\/v850228583\/2945a\/goBRElwhSgw.jpg",
                "type": "x",
                "width": 604
              }
            ]
          },
          "description": "Привет, наши дорогие слушатели! Мы давно обещали сделать еще один специальный выпуск Завтракаста, в котором ответим на накопившиеся вопросы жизни и смерти. Чем занимается Дима в свободное от работы время, как Максим нашел себе жену, зачем Тимур так много фотографирует небо — ответы на эти вопросы вы не узнаете из этого выпуска, зато мы рассказали про многое другое интересное. Надеемся, этот выпуск поможет вам скрасить ожидание до следующего сезона Завтракаста, который должен стартануть уже вот-вот совсем скоро.\n\nНе забывайте, что вы можете подписаться на наш музыкальный подкаст Zavtratunes, в рамках которого у нас на прошлой неделе вышло аж два выпуска сразу. И присылайте свои новые вопросы к нам на почту zavtracast@gmail.com и оставляйте в специально отведенной для этого теме в ВК.",
          "is_favorite": false,
          "plays": 5,
          "position": 0
        },
        "short_videos_allowed": false,
        "stories_allowed": false
      }
    ],
    "profiles": [],
    "groups": [
      {
        "id": 114035565,
        "name": "Zavtracast",
        "screen_name": "zavtracast",
        "is_closed": 0,
        "type": "page",
        "members_count": 10242,
        "photo_50": "https:\/\/sun1-97.userapi.com\/c639223\/v639223461\/3959b\/kT3AnekfIe4.jpg?ava=1",
        "photo_100": "https:\/\/sun1-30.userapi.com\/c639223\/v639223461\/3959a\/8u_BUbTIDls.jpg?ava=1",
        "photo_200": "https:\/\/sun1-98.userapi.com\/c639223\/v639223461\/39599\/HP1unvj0v2c.jpg?ava=1"
      }
    ]
  }
}
  ```
</details>



## podcasts.getStartPage

Главная страница VKUI-приложения "Подкасты".

### Параметры

| Параметр | Тип    | Описание                             |
|----------|--------|--------------------------------------|
| extended | number | Возрат расширенных данных о профилях |
| fields   | string | Возрат полей профилей                |

### Тип возвращаемого значения

Возвращает главную страницу с рекоммендациями и блоками.

```ts
interface VKPodcastCategory {
  id: number
  title: string
  cover: VKCover[]
}

interface VKCover {
  height: number
  width: numbeк
  url: string
}

interface VKPodcastMeta {
  owner_id: number
  podcast_title: string
}

interface VKPodcastCatalogBlock {
  category: VKPodcastCategory
  items: VKPodcastMeta[]
}

interface VKPodcastChartMeta {
  episode: string
  position: number
  diff: number
}

interface VKPodcastChart {
  chart: VKPodcastChartMeta[]
  items: VKAudio[]
}

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
};
```



## podcasts.clearRecentSearches

Очистка истории поиска.

### Тип возвращаемого значения

```ts
type PodcastsClearRecentSearches = number
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": 1
  }
  ```
</details>



## podcasts.getRandomEpisode

Получение случайного эпизода случайного подкаста.

### Тип возвращаемого значения

```ts
type PodcastsGetRandomEpisode = VKAudio
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
  "response": {
    "artist": "theBatya",
    "id": 456242831,
    "owner_id": -36965584,
    "title": "3D-художников не хватает, нейросети нас не заменят, а универсального софта нет",
    "duration": 3057,
    "is_explicit": false,
    "is_focus_track": false,
    "url": "*URL*",
    "date": 1595257408,
    "lyrics_id": 448775225,
    "no_search": 1,
    "podcast_info": {
      "cover": {
        "sizes": [
          {
            "height": 640,
            "url": "https:\/\/sun1-15.userapi.com\/Tnh4tHVpPEOOPebmpDr049xT29GXNUheWsVY2w\/_AVcq3xh7NU.jpg",
            "type": "a",
            "width": 640
          },
          {
            "height": 320,
            "url": "https:\/\/sun1-47.userapi.com\/X17ieiAcn58cFuAvEibZOIbYrIpUqAcfMW5lPw\/vbFAXbIoIKo.jpg",
            "type": "c",
            "width": 320
          },
          {
            "height": 160,
            "url": "https:\/\/sun1-97.userapi.com\/T83ONCZY80o_69jIy54fanB0E6Nh1peg4hLmAg\/Ma7N31Y_70Q.jpg",
            "type": "e",
            "width": 160
          },
          {
            "height": 240,
            "url": "https:\/\/sun1-47.userapi.com\/EXgMSLbA8Ml0lhk4SUATEpxCbpgvwmA4rXxbSw\/uArLxD3kwtI.jpg",
            "type": "b",
            "width": 240
          },
          {
            "height": 120,
            "url": "https:\/\/sun1-27.userapi.com\/Exs2VXzHCnHwB4z56xSDgXR3jSoSvzSoCNzo4g\/X_9zG1aCIJI.jpg",
            "type": "d",
            "width": 120
          },
          {
            "height": 100,
            "url": "https:\/\/sun1-30.userapi.com\/8a1uQVxCh3bCg7jevZH7ieHsMfIv6RQiIv0ZfQ\/_ggMpQwvHTA.jpg",
            "type": "f",
            "width": 100
          },
          {
            "height": 50,
            "url": "https:\/\/sun1-85.userapi.com\/bM7mw1F0OsQFRieSNntpJkIczrAtUiwAXr6SdA\/_U2-BDqWPCs.jpg",
            "type": "h",
            "width": 50
          },
          {
            "height": 1400,
            "url": "https:\/\/sun1-47.userapi.com\/vfFcgaYcy2oMs9npAk12UkApmzd6fq9Zzx7JPA\/X_C5xr1vZ_Q.jpg",
            "type": "x",
            "width": 1400
          }
        ]
      },
      "description": "В гостях Юрий Порубов, 3D-художник по персонажам. Работал как фрилансер над Dragon age Inqisition, Agenst of Mayhem, Overkill's the Walking Dead и Anthem. Портфолио: www.artstation.com\/yuriy_porubov_art\n\nПодкаст на сайте: thebatya.com\/podcasts\/long-live-3d\/\n\nДо 30 сентября XYZ School набирает новичков и любителей 3D-моделирования на курс, обучающий созданию стилизованных персонажей. Курс продлится 5 месяцев, на нём научат всему процессу моделирования, а итоговые работы в портфолио помогут податься на работу. До 28 июля можно записаться с 20% скидкой на любой из трёх типов курсов: просмотр, стандарт и продвинутый. Промокод theBatya даст дополнительные 10% скидки при регистрации вплоть до начала обучения. Страница курса: bit.ly\/3hmqsjz\n\nХотите рассказать интересное или важное об индустрии и играх — пишите на podcast@thebatya.com",
      "is_favorite": false,
      "plays": 81,
      "position": 0,
      "is_random": true
    },
    "short_videos_allowed": false,
    "stories_allowed": false
  }
}
  ```
</details>



## podcasts.markAsListened

Уведомляет ВК, что эпизод прослушан.

### Параметры

| Параметр       | Тип    | Описание                |
|----------------|--------|-------------------------|
| **owner_id**   | number | ID владельца            |
| **episode_id** | number | ID эпизода              |
| ref            | string | Данные для статистики   |

### Тип возвращаемого значения

```ts
type PodcastsMarkAsListened = number
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
      "response": 1
}
  ```
</details>